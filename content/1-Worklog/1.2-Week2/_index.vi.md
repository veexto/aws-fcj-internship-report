---
title: "Nhật ký công việc Tuần 2"
date: 2026-09-21
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---
### Mục tiêu Tuần 2:

- Thành thạo môi trường lập trình đám mây AWS Cloud9 và công cụ dòng lệnh AWS CLI để quản trị tài nguyên.
- Khai thác chuyên sâu dịch vụ lưu trữ đối tượng Amazon S3 (Static Website Hosting, Versioning, Cross-Region Replication) kết hợp mạng phân phối nội dung Amazon CloudFront.
- Triển khai, kết nối và vận hành cơ sở dữ liệu quan hệ trên Amazon RDS kèm các phương án sao lưu, phục hồi dữ liệu.
- Thiết kế kiến trúc có tính sẵn sàng cao (High Availability) và khả năng tự động mở rộng (Scalability) với Launch Template, Application Load Balancer (ALB) và Auto Scaling Group (ASG).

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **Tương tác với dịch vụ AWS qua Cloud9 & CLI** <br> - Khởi tạo môi trường phát triển AWS Cloud9 <br> - Làm quen thao tác trên terminal và quản lý tệp mã nguồn trực tiếp trên đám mây <br> - Thực hành điều khiển các dịch vụ AWS bằng **AWS CLI** <br> - Thu hồi và dọn dẹp tài nguyên sau bài lab | 21/09/2026 | 21/09/2026 | https://000049.awsstudygroup.com/ |
| 3 | **Lưu trữ đối tượng & Phân phối nội dung (S3 & CloudFront)** <br> - Khởi tạo S3 Bucket và tải lên dữ liệu mẫu <br> - Cấu hình **Static Website Hosting** trên Amazon S3 <br> - Kiểm soát quyền truy cập công khai thông qua Block Public Access và Bucket Policy <br> - Tăng tốc độ tải trang toàn cầu bằng **Amazon CloudFront** <br> - Kích hoạt tính năng **S3 Versioning** để chống ghi đè, xóa nhầm dữ liệu <br> - Thực hành di chuyển dữ liệu và cấu hình **Cross-Region Replication (CRR)** | 22/09/2026 | 22/09/2026 | https://000057.awsstudygroup.com/ |
| 4 | **Quản trị Cơ sở dữ liệu Quan hệ (Amazon RDS)** <br> - Chuẩn bị hạ tầng mạng: VPC, Security Group cho EC2 & RDS, và DB Subnet Group <br> - Khởi chạy máy chủ ứng dụng Amazon EC2 <br> - Triển khai cơ sở dữ liệu **Amazon RDS** trong mạng riêng <br> - Cấu hình kết nối từ ứng dụng web trên EC2 tới RDS <br> - Thực hành các kịch bản **sao lưu (Backup) và khôi phục (Restore)** dữ liệu trên RDS | 23/09/2026 | 23/09/2026 | https://000005.awsstudygroup.com/ |
| 5 | **Kiến trúc Tính sẵn sàng cao (High Availability) - Phần 1** <br> - Dựng hạ tầng nền tảng gồm mạng VPC, EC2, RDS và máy chủ web <br> - Tạo **Launch Template** để chuẩn hóa cấu hình khởi tạo máy chủ <br> - Cấu hình **Application Load Balancer (ALB)**: <br>&emsp; + Thiết lập Target Group quản lý các máy chủ đích <br>&
