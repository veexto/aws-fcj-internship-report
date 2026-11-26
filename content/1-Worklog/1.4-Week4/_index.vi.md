---
title: "Nhật ký công việc Tuần 4"
date: 2026-10-05
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---
### Mục tiêu Tuần 4:

- Triển khai kiến trúc **WordPress** chuẩn môi trường production đảm bảo tính sẵn sàng cao (High Availability) và khả năng tự động mở rộng thông qua Auto Scaling Group và Amazon CloudFront.
- Nắm vững quy trình **di chuyển máy chủ (Server Migration)** bằng kỹ thuật VM Import/Export giữa hạ tầng tại chỗ (on-premises) và đám mây AWS.
- Thực hiện **di chuyển cơ sở dữ liệu (Database Migration)** không đồng nhất (heterogeneous) bằng AWS Schema Conversion Tool (SCT) và AWS Database Migration Service (DMS).
- Nghiên cứu các công cụ và chiến lược di chuyển lên đám mây nâng cao (AWS MGN, DataSync, Migration Hub).

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **WordPress trên AWS - Phần 1 (Triển khai nền tảng)** <br> - Chuẩn bị hạ tầng mạng: VPC, Subnet và Security Group tách biệt cho tầng Web và Database <br> - Khởi chạy **Amazon RDS Multi-AZ** để đảm bảo tính dự phòng và sẵn sàng cao cho dữ liệu <br> - Triển khai máy chủ EC2 và cài đặt hoàn chỉnh mã nguồn **WordPress** <br> - Kết nối ứng dụng WordPress trên EC2 tới cơ sở dữ liệu RDS | 05/10/2026 | 05/10/2026 | https://000021.awsstudygroup.com/ |
| 3 | **WordPress trên AWS - Phần 2 (Mở rộng & Tăng tốc CDN)** <br> - Đóng gói **AMI** chuẩn từ máy chủ WordPress đã cấu hình hoàn chỉnh <br> - Thiết lập **Auto Scaling Group (ASG)** kết hợp Application Load Balancer (ALB) <br> - Tối ưu tốc độ tải nội dung toàn cầu bằng **Amazon CloudFront** <br> - Thực hành quy trình sao lưu (Snapshot) và khôi phục dữ liệu RDS <br> - Dọn dẹp toàn bộ tài nguyên thực hành | 06/10/2026 | 06/10/2026 | https://000021.awsstudygroup.com/ |
| 4 | **Di chuyển Máy chủ (VM Import/Export)** <br> - Dựng máy chủ ứng dụng cục bộ để mô phỏng môi trường tại chỗ (on-premises) <br> - **Nhập VM lên AWS (VM Import):** Xuất ảnh VM cục bộ, tải lên S3 và chuyển đổi thành AMI/EC2 <br> - **Xuất VM từ AWS (VM Export):** Xuất ngược EC2 instance về S3 để triển khai lại ở môi trường tại chỗ <br> - Cấu hình S3 ACL và IAM Role phục vụ tác vụ chuyển đổi qua CLI | 07/10/2026 | 07/10/2026 | https://000014.awsstudygroup.com/ |
| 5 | **Di chuyển Cơ sở dữ liệu (AWS DMS & SCT)** <br> - Chuẩn bị môi trường chuyển đổi: cơ sở dữ liệu nguồn (Oracle/SQL Server) và đích (Amazon Aurora/RDS) <br> - Sử dụng **AWS Schema Conversion Tool (SCT)** để chuyển đổi cấu trúc lược đồ giữa hai hệ quản trị khác nhau <br> - Cấu hình **AWS DMS**: <br>&emsp; + Khởi tạo Replication Instance, Source Endpoint và Target Endpoint <br>&emsp; + Thực thi Migration Task kết hợp Full Load và Change Data Capture (CDC) <br> - Trải nghiệm **DMS Serverless** để tự động điều phối tài nguyên sao chép dữ liệu | 08/10/2026 | 08/10/2026 | https://000043.awsstudygroup.com/ |
| 6 | **Giám sát & Chiến lược Di chuyển Nâng cao** <br> - **Giám sát AWS DMS:** Theo dõi chỉ số CloudWatch, thống kê từng bảng (Table Statistics) và nhật ký Task Logs <br> - **Xử lý sự cố:** Chẩn đoán và khắc phục hiện tượng thiếu hụt bộ nhớ (memory pressure) hoặc lỗi ánh xạ bảng trong lúc di chuyển <br> - **Nghiên cứu mở rộng:** Tìm hiểu các mô hình di chuyển hiện đại: <br>&emsp; + AWS Application Migration Service (MGN) <br>&emsp; + AWS DataSync & AWS Migration Hub <br>&emsp; + Lộ trình đưa ứng dụng Container lên Amazon EKS | 09/10/2026 | 09/10/2026 | https://000043.awsstudygroup.com/ <br><br> _Tự nghiên cứu tài liệu AWS Migration Hub_ |

# Kết quả đạt được trong Tuần 4

## Kiến trúc Web chịu tải & Sẵn sàng cao
- Triển khai thành công hệ thống **WordPress** có tính sẵn sàng cao dựa trên **Amazon RDS Multi-AZ** và **Auto Scaling Group**.
- Cấu hình **Application Load Balancer (ALB)** để tự động điều hướng lưu lượng truy cập đến các máy chủ khỏe mạnh.
- Tăng tốc độ phân phối nội dung tĩnh và động tới người dùng cuối thông qua mạng CDN **Amazon CloudFront**.
- Thành thạo quy trình dự phòng thảm họa thông qua thao tác tạo **RDS Snapshot** và khôi phục dữ liệu.

## Di chuyển Hạ tầng Máy chủ (Server Migration)
- Nắm vững quy trình thực tế khi sử dụng bộ công cụ **VM Import/Export** trên AWS.
- Di chuyển thành công máy ảo từ môi trường mô phỏng tại chỗ (VMware) lên vận hành trên Amazon EC2.
- Thực hiện thành công chiều ngược lại: xuất một EC2 instance đang hoạt động thành định dạng ảnh VM di động lưu trên S3.
- Thiết lập chính xác các quyền S3 và IAM Role cần thiết để đảm bảo quá trình chuyển đổi ảnh diễn ra an toàn.

## Di chuyển & Hiện đại hóa Cơ sở dữ liệu
- Triển khai thành công quá trình chuyển đổi cơ sở dữ liệu không đồng nhất (từ SQL Server/Oracle sang Amazon Aurora) bằng **AWS DMS**.
- Áp dụng **AWS Schema Conversion Tool (SCT)** để tự động chuyển đổi schema giữa các nền tảng database khác biệt.
- Cấu hình cơ chế **Change Data Capture (CDC)** giúp đồng bộ dữ liệu liên tục theo thời gian thực, giảm thiểu tối đa thời gian gián đoạn hệ thống (downtime).
- Tìm hiểu cơ chế tự động co giãn tài nguyên của **DMS Serverless** đối với các khối lượng dữ liệu biến động.
- Nắm bắt kỹ thuật giám sát tiến độ di chuyển qua CloudWatch và xử lý các lỗi thường gặp như tràn bộ nhớ hoặc sai lệch kiểu dữ liệu.
