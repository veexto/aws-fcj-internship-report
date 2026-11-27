---
title: "Triển khai Backend AWS Lambda"
date: 2026-11-27
weight: 4
chapter: false
pre: "<b>5.4. </b>"
---

## 1. Khởi tạo hàm Lambda

1. Truy cập **AWS Lambda → Create function → Author from scratch**.
2. Cấu hình thông số cơ bản:
   * **Function name:** `RecipeSearchFunction`
   * **Runtime:** `Python 3.12`
   * **Execution role:** Chọn **Use an existing role** → `RecipesLambdaRole`.
3. Vào **Configuration → General configuration → Edit**, tăng **Timeout** lên `15 seconds`.
4. Vào **Configuration → Environment variables**, thêm 2 biến môi trường:
   * `DYNAMODB_TABLE`: `RecipesTable`
   * `BEDROCK_MODEL_ID`: `apac.amazon.nova-micro-v1:0`

---

## 2. Phân tích kiến trúc & chức năng từng phần trong `lambda_function.py`

Mã nguồn `lambda_function.py` được chia thành **6 khối chức năng chính**, đảm nhiệm toàn bộ luồng từ tiếp nhận HTTP request, xác thực dữ liệu, kết nối 3 dịch vụ lõi của AWS (**DynamoDB**, **Amazon Location Service**, **Amazon Bedrock**) đến trả phản hồi chuẩn JSON về giao diện.

### 2.1. Khởi tạo cấu hình & AWS SDK Clients
* **Vị trí code:** Từ `import base64` đến hết `CORS_HEADERS`.
* **Chức năng chính:**
  * Đọc các biến môi trường (`AWS_REGION`, `BEDROCK_REGION`, `DYNAMODB_TABLE`, `BEDROCK_MODEL_ID`, `BEDROCK_API_KEY`) để tách biệt cấu hình khỏi mã nguồn, dễ thay đổi mà không cần sửa code.
  * Khởi tạo sẵn các kết nối (`boto3.resource` / `boto3.client`) ở phạm vi toàn cục (global scope) gồm: `table` (DynamoDB), `geo_places_client` (Location Service Places v2) và `bedrock_client` (Bedrock Runtime). Việc đặt ngoài `lambda_handler` giúp tái sử dụng kết nối qua các lần gọi **Warm Start**, giảm độ trễ phản hồi.
  * Thiết lập `CORS_HEADERS` cho phép trình duyệt từ tên miền CloudFront gọi API (`GET`, `POST`, `OPTIONS`) mà không bị chặn bởi chính sách bảo mật trình duyệt.

### 2.2. Nhóm hàm tiện ích, Chuẩn hóa & Bảo mật đầu vào
* **Vị trí code:** `json_default()`, `response()`, `normalize()`, `csv_values()`, `query_params()`, `parse_json_body()`.
* **Chức năng chính:**
  * **`json_default()` & `response()`:** Chuyển đổi kiểu số `Decimal` của DynamoDB sang `int`/`float` chuẩn JSON và đóng gói phản hồi HTTP kèm mã trạng thái (`200`, `400`, `500`) và header CORS.
  * **`normalize()`:** Chuẩn hóa chuỗi tiếng Việt về chữ thường không dấu (chuyển `đ -> d`, tách dấu Unicode `NFD`) giúp việc so khớp nguyên liệu và từ khóa tâm trạng chính xác ngay cả khi người dùng gõ thiếu dấu.
  * **`csv_values()`:** Kiểm tra độ dài tối đa (`MAX_INPUT_LENGTH = 200`), giới hạn tối đa 10 từ khóa (`MAX_KEYWORDS = 10`) và loại bỏ các ký tự đặc biệt nguy hiểm (`<>{}$\`\\;`) để chống injection.
  * **`query_params()` & `parse_json_body()`:** Chuẩn hóa cách đọc tham số từ cả hai định dạng sự kiện **API Gateway REST API v1** và **HTTP API v2** (bao gồm cả giải mã Base64 nếu có).

### 2.3. Truy vấn & Lọc công thức nấu ăn (Amazon DynamoDB)
* **Vị trí code:** `get_all_recipes()`, `has_any()`, `has_tag()`, `matches()`, `ingredient_score()`, `handle_recipe_search()`.
* **Chức năng chính:**
  * **`get_all_recipes()`:** Quét toàn bộ dữ liệu từ bảng `RecipesTable` (tự động xử lý phân trang `LastEvaluatedKey` nếu dữ liệu lớn) và sắp xếp theo `RecipeID`.
  * **`matches()`:** Áp dụng bộ lọc đa điều kiện lên từng công thức: nguyên liệu sẵn có (`ingredients`), dị ứng (`allergies`), nguyên liệu cần tránh (`avoid`), chế độ ăn/sức khỏe (`health`, `need`), tâm trạng (`mood`), cùng các ngưỡng số học (`maxTime`, `maxBudget`, `maxSodium`, `maxCarbs`).
  * **`ingredient_score()` & `handle_recipe_search()`:** Chấm điểm mức độ khớp nguyên liệu để ưu tiên đưa các món khớp nhiều nguyên liệu nhất lên đầu danh sách trả về cho tuyến đường `GET /search`.

### 2.4. Định vị & Tìm điểm mua nguyên liệu (Amazon Location Service)
* **Vị trí code:** `haversine_meters()`, `handle_nearby_stores()`.
* **Chức năng chính:**
  * **Xác định tọa độ tâm (`lat`, `lng`):** Nếu người dùng nhập địa chỉ thủ công (`address`), hàm gọi `geo_places_client.geocode()` (và dự phòng bằng `search_text()`) để chuyển đổi chuỗi địa chỉ tiếng Việt sang tọa độ thực tế; nếu để trống thì dùng trực tiếp tọa độ GPS từ trình duyệt.
  * **Truy vấn chuỗi bán lẻ theo ngân sách (`tier`):** Ánh xạ mức ngân sách (`low`, `mid`, `high`) sang các nhóm từ khóa cửa hàng phù hợp (chợ/tạp hóa, Bách Hóa Xanh/WinMart+/Co.op Food, hoặc Co.opmart/Lotte Mart/GO!), sau đó gọi `geo_places_client.search_text()` với `BiasPosition` quanh tọa độ người dùng.
  * **Lọc nhiễu & Tính khoảng cách (`haversine_meters`):** Loại bỏ các địa điểm không phải nơi bán thực phẩm tươi sống (quán cà phê, nhà hàng, spa, trạm xăng...), loại bỏ kết quả trùng tọa độ, tính khoảng cách đường chim bay chính xác theo mét trong bán kính 10 km và sắp xếp từ gần nhất đến xa nhất cho tuyến đường `GET /nearby-stores`.

### 2.5. Chatbot Đầu bếp AI Tâm lý (Amazon Bedrock)
* **Vị trí code:** `find_recipes_by_mood_weather()`, `handle_chat()`.
* **Chức năng chính:**
  * **`find_recipes_by_mood_weather()`:** Phân tích ngữ nghĩa câu nhắn của người dùng (ví dụ: *mưa lạnh, buồn, stress, nắng nóng, mệt mỏi*) để ánh xạ sang các nhóm `MoodTags` (`comforting`, `fresh`, `light`, `energizing`) và loại món ăn tương ứng, đồng thời loại trừ các món đã gợi ý ở lượt trước (`excludeIds`) để tránh lặp lại.
  * **`handle_chat()`:** Đóng gói danh sách thực đơn hiện có từ DynamoDB vào `system_prompt`, gọi mô hình **Amazon Nova Micro** (`apac.amazon.nova-micro-v1:0`) qua `bedrock_client.converse()` (hoặc REST endpoint nếu dùng `BEDROCK_API_KEY`) để sinh câu trả lời đồng cảm, tự nhiên kèm mã món gợi ý (`suggestedRecipeId`) cho tuyến đường `POST /chat`. Có sẵn cơ chế **Fallback** trả về gợi ý định dạng chuẩn nếu Bedrock gặp sự cố mạng hoặc giới hạn quota.

### 2.6. Bộ điều phối trung tâm (`lambda_handler`)
* **Vị trí code:** `lambda_handler(event, context)`.
* **Chức năng chính:**
  * Là điểm vào (Entry Point) duy nhất của hàm Lambda, nhận mọi HTTP request từ API Gateway.
  * Xử lý nhanh yêu cầu preflight `OPTIONS` cho CORS.
  * Phân tuyến (routing) dựa trên phương thức HTTP và đường dẫn:
    * `POST .../chat` → `handle_chat()`
    * `GET .../nearby-stores` → `handle_nearby_stores()`
    * `GET .../search` → `handle_recipe_search()`
  * Bắt lỗi tập trung (`ValueError` trả về `400 Bad Request`, `ClientError` và ngoại lệ hệ thống ghi log ra CloudWatch và trả về `500 Internal Server Error` an toàn).

---

## 3. Bảng tóm tắt luồng xử lý

| Hàm / Khối chức năng | Dịch vụ AWS tương tác | Tuyến đường API | Đầu ra chính |
| :--- | :--- | :--- | :--- |
| `handle_recipe_search` | Amazon DynamoDB (`Scan`) | `GET /search` | Danh sách món ăn đã lọc & xếp hạng khớp nguyên liệu |
| `handle_nearby_stores` | Amazon Location (`Geocode`, `SearchText`) | `GET /nearby-stores` | Tọa độ tâm & danh sách cửa hàng trong 10 km theo ngân sách |
| `handle_chat` | DynamoDB + Amazon Bedrock (`Converse`) | `POST /chat` | Lời tư vấn AI tự nhiên kèm ID món gợi ý mở nhanh |
| `lambda_handler` | API Gateway + CloudWatch Logs | Tất cả routes | Điều phối request, xử lý CORS và bắt lỗi tập trung |
