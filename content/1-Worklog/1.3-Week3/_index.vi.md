---
title: "Nhật ký công việc Tuần 3"
date: 2026-09-28
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---
### Mục tiêu Tuần 3:

- Thiết lập giải pháp giám sát và quan sát hệ thống toàn diện với **Amazon CloudWatch** (Metrics, Logs, Alarms, Dashboards).
- Xây dựng kiến trúc **Hybrid DNS** kết nối mạng nội bộ (on-premises) với hạ tầng đám mây AWS thông qua **Route 53 Resolver** và Microsoft Active Directory.
- Làm chủ **AWS CLI** để tự động hóa việc khởi tạo và quản trị tài nguyên nâng cao xuyên suốt các mảng Lưu trữ, Mạng, Bảo mật và Điện toán.

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **Giám sát & Quan sát hệ thống (Amazon CloudWatch)** <br> - Cấu hình **CloudWatch Metrics**: xem dữ liệu, sử dụng biểu thức tìm kiếm (Search) và biểu thức toán học (Math Expressions) <br> - Truy vấn, phân tích nhật ký với **CloudWatch Logs Insights** và Metric Filters <br> - Thiết lập **CloudWatch Alarms** để cảnh báo chủ động khi tài nguyên vượt ngưỡng <br> - Xây dựng **CloudWatch Dashboard** tập trung theo dõi toàn hệ thống <br> - **Thực hành:** Trực quan hóa hiệu năng EC2 và tạo cảnh báo tự động khi mức sử dụng CPU tăng cao | 28/09/2026 | 28/09/2026 | https://000008.awsstudygroup.com/ |
| 3 | **Mạng lai & Phân giải tên miền (Hybrid DNS)** <br> - Triển khai dịch vụ **Microsoft Active Directory (AD)** trên AWS <br> - Cấu hình **Remote Desktop Gateway (RDGW)** để truy cập quản trị an toàn <br> - Thiết lập kiến trúc **Hybrid DNS** với Route 53 Resolver: <br>&emsp; + Khởi tạo Inbound và Outbound Endpoints <br>&emsp; + Cấu hình Resolver Forwarding Rules <br> - Kiểm thử khả năng phân giải tên miền hai chiều giữa môi trường mô phỏng tại chỗ và AWS | 29/09/2026 | 29/09/2026 | https://000010.awsstudygroup.com/ |
| 4 | **Làm chủ AWS CLI - Phần 1 (Cấu hình & Lưu trữ)** <br> - Cài đặt và cấu hình xác thực cho **AWS CLI v2** <br> - **Tự động hóa Amazon S3:** Quản lý bucket và thực hiện tải tệp dung lượng lớn theo từng phần (Multipart Upload) qua CLI <br> - **Dịch vụ thông báo:** Tạo và quản lý Topic, Subscription trên **Amazon SNS** qua dòng lệnh <br> - Khai thác các định dạng đầu ra (`json`, `table`, `text`) kết hợp bộ lọc `--query` | 30/09/2026 | 30/09/2026 | https://000011.awsstudygroup.com/ <br><br> https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-troubleshooting.html |
| 5 | **Làm chủ AWS CLI - Phần 2 (Điện toán & Hạ tầng mạng)** <br> - **
