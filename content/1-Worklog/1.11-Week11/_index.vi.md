---
title: "Nhật ký công việc Tuần 11"
date: 2026-11-23
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu Tuần 11:
- Tích hợp giao diện người dùng (frontend) với các API backend có yêu cầu xác thực bảo mật.
- Nâng cấp cơ chế bắt và xử lý ngoại lệ đồng bộ trên cả **API Gateway** và **AWS Lambda**.
- Thiết kế giải pháp lưu trữ token an toàn phía client kèm luồng làm mới phiên (refresh token) tự động.
- Xây dựng lớp API Client dùng chung (Axios/Fetch) tích hợp sẵn các bộ chặn (interceptors).
- Cải thiện khả năng thu thập log, truy vết lỗi và giám sát hiệu năng thông qua **Amazon CloudWatch**.
- Hoàn thiện luồng tương tác full-stack khép kín từ UI → API Gateway → Lambda → DynamoDB.

---

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|-----|-----------|---------------|------------------|---------------------|
| 2 | - Kết nối ứng dụng frontend với các endpoint xác thực của **Amazon Cognito** <br>- Thiết kế và hoàn thiện giao diện màn hình đăng ký, đăng nhập tài khoản | 23/11/2026 | 23/11/2026 | AWS Study Group |
| 3 | - Triển khai cơ chế lưu trữ token an toàn và tự động cấp lại token khi hết hạn (refresh token) <br>- Tích hợp request/response interceptors vào API Client trung tâm | 24/11/2026 | 24/11/2026 | AWS Study Group |
| 4 | - Kết nối frontend với các endpoint được bảo vệ trên **API Gateway** <br>- Kiểm thử thực tế luồng xác minh quyền truy cập qua **Lambda Authorizer** | 25/11/2026 | 25/11/2026 | AWS Study Group |
| 5 | - Xây dựng cơ chế xử lý lỗi tập trung (Global Error Handling) xuyên suốt từ backend lên frontend <br>- Chuẩn hóa cấu trúc dữ liệu phản hồi và mã lỗi API | 26/11/2026 | 26/11/2026 | AWS Study Group |
| 6 | - Tăng cường giám sát vận hành với **CloudWatch Logs & Metrics** <br>- Rà soát, gỡ lỗi và tối ưu hóa toàn bộ luồng dữ liệu đầu–cuối (End-to-End) | 27/11/2026 | 27/11/2026 | AWS Study Group |

---

### Kết quả đạt được trong Tuần 11:

#### **1. Tích hợp thành công Frontend với Amazon Cognito**
Kết nối hoàn chỉnh giao diện người dùng với dịch vụ định danh Cognito, hỗ trợ đầy đủ các nghiệp vụ đăng ký, đăng nhập và đăng xuất trực tiếp trên ứng dụng. Quá trình khởi tạo phiên và cấp phát token diễn ra ổn định.

#### **2. Lưu trữ Token an toàn & Cơ chế Refresh tự động**
Áp dụng phương thức lưu trữ token an toàn trên trình duyệt kết hợp luồng tự động làm mới phiên khi Access Token hết hạn. Lớp interceptor được cấu hình để tự động đính kèm token xác thực vào tiêu đề (header) của mọi yêu cầu gửi đi.

#### **3. Kết nối Frontend với hệ thống API được bảo vệ**
Giao diện người dùng đã có thể giao tiếp an toàn với các route yêu cầu xác thực JWT trên API Gateway, hoàn thiện chuỗi bảo mật xuyên suốt từ UI → API Client → API Gateway → Lambda → DynamoDB.

#### **4. Chuẩn hóa hệ thống Xử lý Lỗi Toàn cục**
Thống nhất định dạng phản hồi lỗi từ các hàm Lambda, tinh chỉnh mapping trên API Gateway và xây dựng bộ xử lý lỗi tập trung ở frontend để hiển thị thông báo trực quan cho người dùng, giúp cải thiện trải nghiệm và rút ngắn thời gian gỡ lỗi.

#### **5. Nâng cao khả năng Giám sát & Gỡ lỗi với CloudWatch**
Khai thác dữ liệu từ CloudWatch Logs để phát hiện các điểm nghẽn hiệu năng, đồng thời thiết lập Metric Filters theo dõi tỷ lệ lỗi và độ trễ phản hồi của các hàm Lambda, giúp quy trình vận hành chủ động hơn.

#### **6. Vận hành hoàn chỉnh luồng Full-Stack Xác thực & Dữ liệu**
Kiểm thử thành công trọn vẹn quy trình nghiệp vụ thực tế:  
UI → Xác thực Cognito → Gửi API Request → Lambda xử lý → DynamoDB lưu trữ/truy xuất → Trả kết quả hiển thị.  
Hệ thống vận hành ổn định, đáp ứng đầy đủ các tiêu chuẩn bảo mật và kiểm soát ngoại lệ.

---
