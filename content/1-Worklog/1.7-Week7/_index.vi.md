---
title: "Nhật ký công việc Tuần 7"
date: 2026-10-26
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---
### Mục tiêu Tuần 7:

- **Đóng gói Ứng dụng (Containerization):** Làm chủ quy trình đóng gói ứng dụng bằng **Docker** và quản lý image tập trung trên Amazon ECR.
- **Điều phối Container (Orchestration):** Triển khai và vận hành các cụm container có khả năng mở rộng linh hoạt trên **Amazon ECS (Elastic Container Service)**.
- **DevOps & Tự động hóa CI/CD:** Xây dựng đường ống **CI/CD Pipelines** (AWS CodePipeline, CodeBuild, CodeDeploy) để tự động hóa quy trình build và triển khai lên EC2 lẫn ECS.
- **Giải pháp Lưu trữ Lai (Hybrid Storage):** Kết nối hạ tầng tại chỗ với đám mây AWS thông qua **AWS Storage Gateway (File Gateway)** và **Amazon FSx for Windows File Server**.
- **Thiết kế Cơ sở dữ liệu NoSQL Nâng cao:** Nắm vững mô hình hóa dữ liệu, chiến lược đánh chỉ mục và tối ưu hiệu năng truy vấn trên **Amazon DynamoDB**.

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **Đóng gói Ứng dụng với Docker & Amazon ECR** <br> - Cài đặt môi trường Docker trên máy cục bộ và máy chủ EC2 <br> - Viết Dockerfile để đóng gói các thành phần ứng dụng mẫu (Frontend/Backend) <br> - Sử dụng **Docker Compose** để khởi chạy và điều phối đồng thời nhiều container <br> - Đẩy (Push) các Docker image lên kho lưu trữ **Amazon ECR** | 26/10/2026 | 26/10/2026 | https://000015.awsstudygroup.com/ |
| 3 | **Điều phối Container trên Amazon ECS** <br> - Khởi tạo **ECS Cluster** (hỗ trợ cả hai mô hình Fargate và EC2) <br> - Thiết lập **Task Definitions** và cấu hình ECS Services duy trì số lượng container <br> - Tích hợp **Application Load Balancer (ALB)** để cân bằng tải lưu lượng truy cập <br> - Cấu hình cơ chế **Service Discovery** thông qua **AWS Cloud Map** | 27/10/2026 | 27/10/2026 | https://000016.awsstudygroup.com/ |
| 4 | **Tự động hóa CI/CD cho Hệ thống Container** <br> - Thiết lập **AWS CodePipeline** tự động kích hoạt khi có commit mới từ GitHub/GitLab <br> - Cấu hình **AWS CodeBuild** để tự động đóng gói Docker image và đẩy lên ECR <br> - Triển khai cập nhật tự động (Rolling Update) lên cụm ECS Cluster <br> - Giám sát tài nguyên container với **CloudWatch Container Insights** và thu thập log bằng **FireLens** | 28/10/2026 | 28/10/2026 | https://000017.awsstudygroup.com/ |
| 5 | **CI/CD cho EC2 & Lưu trữ Lai (Hybrid Storage)** <br> - **CodePipeline cho EC2:** Tự động hóa triển khai mã nguồn thông qua CodeDeploy Agent <br> - **AWS Storage Gateway:** Triển khai File Gateway để ánh xạ S3 bucket thành ổ đĩa chia sẻ giao thức NFS <br> - **Amazon FSx:** Khởi tạo hệ thống tệp **FSx for Windows File Server** được quản lý hoàn toàn và kết nối qua giao thức SMB | 29/10/2026 | 29/10/2026 | https://000023.awsstudygroup.com/ <br><br> _Tự nghiên cứu tài liệu FSx & Storage Gateway_ |
| 6 | **Kiến trúc & Tối ưu Amazon DynamoDB Nâng cao** <br> - **Mô hình hóa dữ liệu:** Áp dụng tư duy thiết kế **Single Table Design** cho hệ thống NoSQL <br> - **Tối ưu hiệu năng:** Thiết kế Partition Key, Sort Key hợp lý và tính toán năng lực đọc/ghi (RCU/WCU) <br> - **Tính năng nâng cao:** Triển khai Global Secondary Indexes (GSI), DynamoDB Streams và Global Tables | 30/10/2026 | 30/10/2026 | https://000039.awsstudygroup.com/ |

# Kết quả đạt được trong Tuần 7

## Đóng gói & Điều phối Container
- Đóng gói thành công ứng dụng thành các **Docker Image** độc lập, loại bỏ sự phụ thuộc vào cấu hình môi trường hạ tầng bên dưới.
- Triển khai cụm dịch vụ container có tính sẵn sàng cao với **Amazon ECS**, quản lý chặt chẽ tài nguyên CPU/RAM thông qua Task Definitions.
- Cấu hình **Service Discovery** với AWS Cloud Map, giúp các dịch vụ nội bộ giao tiếp bằng tên miền logic thay vì phụ thuộc vào địa chỉ IP động.
- Tích hợp **Application Load Balancer** để phân phối lưu lượng người dùng một cách linh hoạt tới các container đang hoạt động.

## Tự động hóa DevOps & Đường ống CI/CD
- Xây dựng hoàn chỉnh quy trình **CI/CD Pipeline** khép kín bằng AWS CodePipeline và CodeBuild.
- Đạt được khả năng **Continuous Deployment**: mỗi thay đổi mã nguồn đẩy lên Git tự động kích hoạt build image mới và cập nhật dịch vụ ECS theo cơ chế rolling update không gián đoạn (zero downtime).
- Giám sát chi tiết hiệu năng từng task/container thông qua **CloudWatch Container Insights**.
- Chuẩn hóa luồng thu thập và tập trung log từ container bằng **FireLens** phục vụ việc truy vết và xử lý lỗi nhanh chóng.

## Tích hợp Lưu trữ Lai (Hybrid Storage)
- Kết nối liền mạch các giao thức lưu trữ truyền thống tại chỗ với kho lưu trữ đám mây AWS.
- Triển khai **File Storage Gateway** giúp các ứng dụng hiện hữu lưu trữ dữ liệu trực tiếp lên Amazon S3 thông qua giao thức NFS quen thuộc.
- Vận hành **Amazon FSx for Windows File Server**, cung cấp hệ thống chia sẻ tệp chuẩn Windows hỗ trợ giao thức SMB và tích hợp sẵn Active Directory.

## Thiết kế Cơ sở dữ liệu NoSQL Hiệu năng cao
- Nắm vững tư duy thiết kế và vận hành cơ sở dữ liệu phi quan hệ trên **Amazon DynamoDB**.
- Tối ưu hóa tốc độ truy vấn và phân bổ dữ liệu đồng đều nhờ lựa chọn **Partition Key** và **Sort Key** phù hợp.
- Mở rộng khả năng truy vấn đa chiều bằng **Global Secondary Indexes (GSI)** mà không làm dư thừa dữ liệu gốc.
- Ứng dụng **DynamoDB Streams** để xây dựng luồng xử lý hướng sự kiện (Event-Driven), tự động kích hoạt AWS Lambda ngay khi bản ghi có sự thay đổi.
