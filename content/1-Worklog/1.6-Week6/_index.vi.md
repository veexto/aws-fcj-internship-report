---
title: "Nhật ký công việc Tuần 6"
date: 2026-10-19
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---
### Mục tiêu Tuần 6:

- **Quản trị Danh tính & Truy cập Nâng cao (IAM):** Thiết lập đăng nhập tập trung với **IAM Identity Center (SSO)**, kiểm soát ngưỡng đặc quyền tối đa bằng **Permission Boundaries** và ràng buộc điều kiện chặt chẽ khi chuyển giao vai trò (IAM Role Conditions).
- **Giám sát Tuân thủ & Bảo vệ Ứng dụng:** Tự động hóa đánh giá tiêu chuẩn bảo mật bằng **AWS Security Hub** và ngăn chặn tấn công tầng ứng dụng với **AWS WAF**.
- **Bảo vệ & Dự phòng Dữ liệu:** Làm chủ cơ chế mã hóa khóa riêng với **AWS KMS** kết hợp kiểm toán truy vết, đồng thời chuẩn hóa chính sách sao lưu tập trung qua **AWS Backup**.
- **Kiến trúc Mạng Quy mô lớn:** Triển khai kết nối liên mạng giữa các VPC theo mô hình điểm-nối-điểm (**VPC Peering**) và mô hình trục-nan (**AWS Transit Gateway**).

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **Quản trị Danh tính & Phân quyền Nâng cao** <br> - Triển khai **IAM Identity Center (SSO)** để quản lý truy cập tập trung xuyên suốt nhiều tài khoản AWS <br> - Thiết lập **Permission Boundaries** nhằm giới hạn trần quyền hạn tối đa cho IAM User/Role <br> - Bổ sung **IAM Role Conditions** (như `iam:PassedToService`) để ngăn chặn hành vi lạm dụng chuyển tiếp vai trò | 19/10/2026 | 19/10/2026 | https://000012.awsstudygroup.com/ <br><br> https://000030.awsstudygroup.com/ <br><br> https://000044.awsstudygroup.com/ |
| 3 | **Đánh giá Tuân thủ & Tường lửa Ứng dụng Web** <br> - Kích hoạt **AWS Security Hub** để quét và chấm điểm mức độ tuân thủ theo bộ tiêu chuẩn CIS <br> - Triển khai **AWS WAF** bảo vệ tầng biên ứng dụng: <br>&emsp; + Khởi tạo Web ACL tích hợp các bộ quy tắc quản lý sẵn (Managed Rule Groups) <br>&emsp; + Cấu hình chặn các cuộc tấn công SQL Injection và XSS trước khi đi vào Application Load Balancer | 20/10/2026 | 20/10/2026 | https://000018.awsstudygroup.com/ <br><br> https://000026.awsstudygroup.com/ |
| 4 | **Mã hóa Dữ liệu & Sao lưu Tập trung (KMS & AWS Backup)** <br> - Khởi tạo Customer Managed Keys (CMK) trên **AWS KMS** để tự chủ quản lý vòng đời khóa mã hóa <br> - Áp dụng mã hóa phía máy chủ cho S3 Bucket và truy vết lịch sử gọi khóa qua **CloudTrail** kết hợp **Amazon Athena** <br> - Thiết lập chính sách dự phòng với **AWS Backup**: <br>&emsp; + Tạo Backup Vault lưu trữ an toàn và xây dựng Backup Plan định kỳ <br>&emsp; + Thực hành sao lưu theo yêu cầu (On-demand) và diễn tập khôi phục dữ liệu | 21/10/2026 | 21/10/2026 | https://000033.awsstudygroup.com/ <br><br> https://000013.awsstudygroup.com/ |
| 5 | **Kết nối Mạng Liên vùng & Mô hình Hub-and-Spoke** <br> - **VPC Peering:** Thiết lập kênh kết nối riêng tư trực tiếp giữa hai VPC độc lập, cập nhật Route Tables và tùy chọn phân giải DNS nội bộ <br> - **AWS Transit Gateway (TGW):** Xây dựng bộ định tuyến trung tâm kết nối đồng thời nhiều VPC <br> - Cấu hình phân tách **TGW Route Tables** để cô lập luồng lưu lượng giữa các môi trường mạng | 22/10/2026 | 22/10/2026 | https://000019.awsstudygroup.com/ <br><br> https://000020.awsstudygroup.com/ |
| 6 | **Kiểm tra Bảo mật & Thu hồi Tài nguyên** <br> - Rà soát tổng thể các thiết lập phân quyền, tường lửa và mã hóa đã triển khai <br> - **Dọn dẹp tài nguyên:** Gỡ bỏ Transit Gateway, NAT Gateways và vô hiệu hóa Security Hub / AWS Config để tránh phát sinh chi phí duy trì <br> - Đặt lịch hủy (Schedule Deletion) cho các khóa CMK trên AWS KMS | 23/10/2026 | 23/10/2026 | _Tổng hợp các mục Dọn dẹp tài nguyên cuối bài lab_ |

# Kết quả đạt được trong Tuần 6

## Quản trị Danh tính & Kiểm soát Đặc quyền (IAM)
- Vận hành thành công **IAM Identity Center**, đơn giản hóa trải nghiệm đăng nhập một lần (SSO) và quản lý tập trung danh tính người dùng.
- Ngăn ngừa hiệu quả rủi ro leo thang đặc quyền nhờ áp dụng **Permission Boundaries**, đảm bảo tài khoản được ủy quyền không thể tự mở rộng quyền vượt ngưỡng cho phép.
- Siết chặt an toàn vận hành bằng việc gắn **Conditions** vào IAM Roles, kiểm soát chặt chẽ bối cảnh và dịch vụ đích được phép tiếp nhận vai trò.

## Tuân thủ Bảo mật & Phòng thủ Tầng Ứng dụng
- Kích hoạt **AWS Security Hub** để giám sát tập trung trạng thái an toàn thông tin và tự động đối chiếu hạ tầng với chuẩn **CIS AWS Foundations Benchmark**.
- Gia cố lớp phòng vệ biên cho ứng dụng web bằng **AWS WAF**, lọc và loại bỏ thành công lưu lượng độc hại (SQL Injection, XSS, IP xấu) ngay trước ngưỡng cửa Application Load Balancer.

## Mã hóa Dữ liệu & Chiến lược Phục hồi Thảm họa
- Làm chủ quy trình bảo vệ dữ liệu nhạy cảm trên S3 thông qua **Customer Managed Keys (CMK)** của **AWS KMS**.
- Xây dựng luồng kiểm toán minh bạch bằng cách đẩy nhật ký sử dụng khóa KMS sang **AWS CloudTrail** và dùng **Amazon Athena** để truy vấn phân tích.
- Thiết lập cơ chế sao lưu tự động và phục hồi thảm họa (DR) đồng bộ thông qua **AWS Backup**, kiểm thử thành công việc khôi phục nguyên trạng EBS Volume từ điểm sao lưu.

## Thiết kế Hạ tầng Mạng Mở rộng
- Triển khai kết nối mạng riêng tư tốc độ cao giữa hai VPC tách biệt qua **VPC Peering**, loại bỏ hoàn toàn việc truyền tải dữ liệu nội bộ qua Internet công cộng.
- Giải quyết bài toán kết nối chằng chịt (full-mesh) khi mở rộng nhiều VPC bằng kiến trúc hub-and-spoke sử dụng **AWS Transit Gateway**.
- Tinh chỉnh thành thạo hệ thống **Route Tables** trên cả VPC và Transit Gateway để điều hướng chính xác và đảm bảo phân tách lưu lượng giữa các phân vùng mạng.
