---

#### File `5-Workshop/5.04-deploy-lambda-backend/_index.md`
```markdown
---
title: "Triển khai Backend AWS Lambda"
date: 2026-11-27
weight: 4
chapter: false
pre: "<b>5.4. </b>"
---

#### Tạo hàm Lambda

1. Truy cập **AWS Lambda → Create function → Author from scratch**.
2. Cấu hình thông số cơ bản:
   * **Function name:** `RecipeSearchFunction`
   * **Runtime:** `Python 3.12`
   * **Execution role:** Chọn **Use an existing role** → `RecipesLambdaRole`.
3. Vào **Configuration → General configuration → Edit**, tăng **Timeout** lên `15 seconds`.
4. Vào **Configuration → Environment variables**, thêm 2 biến môi trường:
   * `DYNAMODB_TABLE`: `RecipesTable`
   * `BEDROCK_MODEL_ID`: `apac.amazon.nova-micro-v1:0`

#### Luồng xử lý chính trong `lambda_function.py`

* **`handle_recipe_search`:** Quét danh sách công thức từ `RecipesTable`, chuẩn hóa chuỗi tiếng Việt không dấu để tìm kiếm nguyên liệu và lọc theo ngân sách, thời gian nấu, tâm trạng.
* **`handle_nearby_stores`:** Chuyển đổi địa chỉ nhập tay sang tọa độ qua `geo_places_client.geocode`, sau đó truy vấn chuỗi cửa hàng/siêu thị theo phân khúc ngân sách (`low`, `mid`, `high`) bằng `geo_places_client.search_text` và sắp xếp theo khoảng cách Haversine.
* **`handle_chat`:** Gửi danh sách thực đơn làm ngữ cảnh cho `bedrock_client.converse` để Đầu bếp AI gợi ý món ăn phù hợp tâm trạng và thời tiết.

5. Dán mã nguồn `lambda_function.py` vào tab **Code** và bấm **Deploy**.
