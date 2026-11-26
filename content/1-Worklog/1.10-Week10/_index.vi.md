---
title: "Nhật ký công việc Tuần 10"
date: 2026-11-16
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu Tuần 10:
- Nâng cao năng lực bảo mật tầng backend và chuẩn hóa luồng xác thực trên hạ tầng đám mây.
- Hoàn thiện tích hợp **Amazon Cognito** với kiến trúc phân quyền dựa trên mã thông báo (Token-based Authentication).
- Bổ sung cơ chế kiểm tra tính hợp lệ dữ liệu (validation), tối ưu mẫu truy xuất (access patterns) và chỉ mục phụ cho **Amazon DynamoDB**.
- Cấu hình lớp kiểm soát truy cập thông qua Authorizer, giới hạn lưu lượng (Throttling) và Rate Limit trên **API Gateway**.
- Liên kết đồng bộ các thành phần backend thành một quy trình vận hành khép kín.

---

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|-----|-----------|--------------|------------------|--------------------|
| 2 | - Nghiên cứu chuyên sâu cơ chế xác thực/phân quyền (JWT, Access Token, ID Token) <br>- Rà soát các tiêu chuẩn bảo mật theo danh mục **OWASP API Security Top 10** | 16/11/2026 | 16/11/2026 | AWS Study Group |
| 3 | - Tìm hiểu kiến trúc và phân biệt vai trò của **Cognito User Pool** và **Identity Pool** <br>- Triển khai hoàn chỉnh các luồng đăng ký (sign-up), đăng nhập (sign-in) và làm mới phiên (refresh token) | 17/11/2026 | 17/11/2026 | AWS Study Group |
| 4 | - Lập trình **Lambda Authorizer** tùy chỉnh để kiểm tra tính hợp lệ của token và gắn vào API Gateway <br>- Cấu hình phân quyền IAM Policy chính xác cho quá trình thực thi | 18/11/2026 | 18/11/2026 | AWS Study Group |
| 5 | - Nâng cấp thiết kế bảng **Amazon DynamoDB**: <br>&emsp; + Bổ sung Global Secondary Index (GSI) phục vụ các truy vấn đa chiều <br>&emsp; + Siết chặt kiểm tra dữ liệu đầu vào và chuẩn hóa xử lý ngoại lệ (error handling) | 19/11/2026 | 19/11/2026 | AWS Study Group |
| 6 | - Kiểm thử tích hợp toàn trình (End-to-End Testing): <br>&emsp; + Client → API Gateway → Lambda Authorizer / Handler → DynamoDB | 20/11/2026 | 20/11/2026 | AWS Study Group |

---

### Kết quả đạt được trong Tuần 10:

#### **1. Củng cố kiến thức Bảo mật & Cơ chế Xác thực API**
Nắm vững cấu trúc và vòng đời của JWT, phân biệt rõ chức năng giữa Access Token, ID Token và Refresh Token, đồng thời áp dụng các biện pháp phòng vệ theo chuẩn OWASP để giảm thiểu lỗ hổng bảo mật ở tầng giao tiếp API.

#### **2. Hoàn thiện luồng Định danh với Amazon Cognito**
Thiết lập trơn tru quy trình đăng ký tài khoản, đăng nhập, xác thực đa yếu tố (MFA) và cấp lại token tự động trên Cognito. Toàn bộ kịch bản đã được kiểm thử kỹ lưỡng thông qua Postman và AWS CLI.

#### **3. Bảo vệ Endpoint bằng Custom Lambda Authorizer**
Xây dựng thành công hàm Lambda Authorizer đóng vai trò chốt chặn xác minh chữ ký và quyền hạn từ token trước khi chuyển tiếp yêu cầu vào hệ thống xử lý lõi, ngăn chặn triệt để các truy cập trái phép.

#### **4. Tối ưu hóa truy vấn DynamoDB với Secondary Index**
Bổ sung Global Secondary Index (GSI) giúp mở rộng linh hoạt các điều kiện lọc dữ liệu mà vẫn giữ độ trễ truy vấn ở mức thấp, kết hợp lớp validation chặt chẽ nhằm bảo toàn tính nhất quán của dữ liệu.

#### **5. Vận hành thông suốt quy trình Backend Đầu–Cuối**
Kiểm chứng thành công luồng dữ liệu khép kín từ phía Client gửi yêu cầu qua API Gateway, xác thực quyền hạn, xử lý logic tại AWS Lambda, lưu trữ/truy xuất trên DynamoDB và trả về phản hồi chính xác.

#### **6. Tái cấu trúc mã nguồn (Refactoring) nâng cao khả năng bảo trì**
Tổ chức lại cấu trúc mã nguồn các hàm Lambda theo hướng phân tách trách nhiệm rõ ràng giữa tầng điều phối (handler), tầng kiểm tra dữ liệu (validation) và tầng thao tác cơ sở dữ liệu, giúp dễ dàng mở rộng và gỡ lỗi về sau.

---
