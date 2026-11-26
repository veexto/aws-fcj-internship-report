---
title: "Blog Kỹ Thuật AWS"
date: 2026-09-14
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Trang này tổng hợp **3 bài viết kỹ thuật chuyên sâu** được đúc kết từ quá trình thực hành lab, kiểm thử tải và xử lý các bài toán vận hành thực tế trên nền tảng **Amazon Web Services (AWS)**:

### [Blog 1 - Web đã Auto Scaling ngon lành, sao 10.000 user vào vẫn xoay vòng vòng?](3.1-Blog1/)
Bài viết bóc tách nguyên nhân gây nghẽn cổ chai ở tầng cơ sở dữ liệu khi hệ thống Web mở rộng ngang qua **Auto Scaling Group** dưới tải 10.000 người dùng đồng thời. Qua đó, bài viết trình bày giải pháp tối ưu luồng đọc theo hai lớp gồm **Amazon ElastiCache (Redis)** áp dụng chiến lược **Cache-Aside (Lazy Loading)** và **Amazon RDS Read Replicas** để san tải truy vấn, đồng thời phân tích 4 cạm bẫy thực tế khi triển khai như nhầm lẫn giữa Multi-AZ Standby với Read Replica, độ trễ đồng bộ (Replication Lag), hiệu ứng Cache Stampede và quản lý chi phí tại region Singapore (`ap-southeast-1`).

### [Blog 2 - S3 và EC2 nằm cùng Region, sao hóa đơn NAT Gateway vẫn nhảy tiền mỗi tháng?](3.2-Blog2/)
Bài viết phân tích bẫy chi phí truyền dữ liệu nội bộ khi các máy chủ trong **Private Subnet** giao tiếp với **Amazon S3** và **Amazon DynamoDB** qua tuyến đường mặc định `0.0.0.0/0` đi xuyên qua **NAT Gateway**. Bài viết giải thích cơ chế định tuyến **Longest Prefix Match** của **VPC Gateway Endpoint** giúp giữ toàn bộ lưu lượng nội bộ chạy trên mạng xương sống AWS với chi phí **0 USD/GB**, kèm theo 4 lưu ý kỹ thuật quan trọng về phân biệt Gateway/Interface Endpoint, gắn Route Table, giới hạn cùng Region và cấu hình ngoại lệ `aws:PrincipalArn` khi siết Bucket Policy bằng `aws:SourceVpce`.

### [Blog 3 - Chạy lại pipeline tuần trước mà ra số khác hẳn: Do code sửa hay do file trên S3 bị ghi đè?](3.3-Blog3/)
Bài viết giải quyết bài toán **tái lập dữ liệu (Data Reproducibility)** cho các luồng ETL và huấn luyện mô hình AI/ML trên AWS khi dữ liệu nguồn trên S3 liên tục bị ghi đè. Thay vì phụ thuộc vào trường `ETag` dễ sai lệch với Multipart Upload hoặc mã hóa KMS, bài viết đề xuất kiến trúc kết hợp **Amazon S3 Versioning** (ghim cố định `VersionId`) cùng bảng kê **Manifest trên Amazon DynamoDB** lưu mã băm **SHA-256** để kiểm tra toàn vẹn theo cơ chế **Fail Fast**, đi kèm các lưu ý về quyền `s3:GetObjectVersion` và dọn dẹp phiên bản cũ bằng **S3 Lifecycle Rule**.
