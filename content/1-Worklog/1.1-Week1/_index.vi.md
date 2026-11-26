---
title: "Nhật ký công việc Tuần 1"
date: 2026-09-14
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
### Mục tiêu Tuần 1:

- Hòa nhập cùng đội ngũ thực tập sinh và mentor tại First Cloud Journey.
- Nắm vững kiến trúc tổng quan của các nhóm dịch vụ lõi trên AWS và thao tác thành thạo trên Console lẫn CLI.

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ---------------------------------------------------------------------------------- |
| 2 | - Giao lưu, làm quen với các thành viên trong chương trình FCJ <br> - Nghiên cứu nội quy, quy trình làm việc và văn hóa tại đơn vị thực tập | 14/09/2026 | 14/09/2026 | |
| 3 | - Tìm hiểu hệ sinh thái dịch vụ lõi trên AWS: <br>&emsp; + Compute <br>&emsp; + Storage <br>&emsp; + Networking <br>&emsp; + Database <br> - Luyện tập thiết kế sơ đồ kiến trúc hệ thống AWS bằng công cụ draw.io <br> - Nắm quy trình triển khai các bài lab AWS Workshop <br /><br> | 15/09/2026 | 15/09/2026 | https://cloudjourney.awsstudygroup.com/ <br> <br> https://www.youtube.com/watch?v=l8isyDe-GwY&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=2 <br> <br> https://www.youtube.com/watch?v=mXRqgMr_97U&list=PLahN4TLWtox2a3vElknwzU_urND8hLn1i&index=3|
| 4 | - Khởi tạo tài khoản AWS mới phục vụ thực hành <br> - Giám sát và kiểm soát chi phí đám mây thông qua AWS Budgets <br> - Tìm hiểu quy trình gửi yêu cầu hỗ trợ kỹ thuật với AWS Support <br> - **Thực hành:** <br>&emsp; + Cấu hình tài khoản AWS ban đầu, kích hoạt xác thực đa yếu tố (MFA), khởi tạo nhóm và tài khoản quản trị (Admin) <br>&emsp; + Thiết lập các mẫu ngân sách theo dõi: Cost Budget, Usage Budget, RI Budget và Savings Plans Budget <br>&emsp; + Thực hành chuyển đổi gói hỗ trợ và khởi tạo Support Case mẫu <br> | 16/09/2026 | 16/09/2026 | https://000001.awsstudygroup.com/ <br> <br> https://000007.awsstudygroup.com/ <br> <br> https://000009.awsstudygroup.com/ |
| 5 | - Phân quyền và quản lý danh tính người dùng với AWS Identity and Access Management (AWS IAM) <br> - Xây dựng hạ tầng mạng ảo cô lập với Amazon Virtual Private Cloud (Amazon VPC): <br>&emsp; + Cơ chế tường lửa và bảo mật tầng mạng trong VPC <br>&emsp; + Triển khai máy chủ ảo Amazon EC2 trong mạng riêng <br>&emsp; + Cấu hình kết nối Site-to-Site VPN trên AWS <br> - **Thực hành:** <br>&emsp; + Thiết lập hoàn chỉnh kiến trúc VPC gồm Public/Private Subnet, Internet Gateway, Route Table, Security Group, EC2, NAT Gateway và kết nối VPN | 17/09/2026 | 17/09/2026 | https://000002.awsstudygroup.com/ <br><br> https://000003.awsstudygroup.com/ |
| 6 | - Khởi tạo và vận hành ứng dụng trên Amazon Elastic Compute Cloud (Amazon EC2): <br>&emsp; + Cài đặt máy chủ Microsoft Windows Server 2022 <br>&emsp; + Triển khai ứng dụng quản lý người dùng trên nền tảng Amazon Linux 2 <br>&emsp; + Chạy ứng dụng Node.js trên môi trường EC2 Windows <br>&emsp; + Kiểm soát chi phí và quyền hạn sử dụng tài nguyên bằng IAM <br> - Phân quyền cho ứng dụng giao tiếp với các dịch vụ AWS thông qua IAM Role <br> - **Thực hành:** <br>&emsp; + Truy cập từ xa vào Windows Server 2022 và Amazon Linux, triển khai môi trường web LAMP/XAMPP <br>&emsp; + Khởi tạo và cấu hình lưu trữ đối tượng với Amazon S3 bucket | 18/09/2026 | 18/09/2026 | https://000004.awsstudygroup.com/ <br><br> https://000048.awsstudygroup.com/ |

# Kết quả đạt được trong Tuần 1

## Hòa nhập & Định hướng
- Kết nối thành công với các thành viên và mentor trong cộng đồng First Cloud Journey  
- Nắm rõ quy định vận hành, kỷ luật và lộ trình thực tập  

## Kiến thức nền tảng AWS
- Hệ thống hóa được vai trò của 4 nhóm dịch vụ trọng tâm: **Compute, Storage, Networking, Database**  
- Thành thạo thao tác vẽ sơ đồ kiến trúc đám mây chuẩn AWS bằng **draw.io**  
- Nắm vững phương pháp tiếp cận và thực hành các bài lab từ kho tài liệu AWS Study Group  

## Khởi tạo tài khoản & Quản trị chi phí
- Thiết lập hoàn chỉnh tài khoản AWS Free Tier sẵn sàng cho môi trường lab  
- Tăng cường bảo mật tài khoản gốc bằng **Multi-Factor Authentication (MFA)**  
- Phân tách quyền quản trị thông qua việc tạo **Admin Group** và **Admin User** thay vì dùng tài khoản Root  
- Cấu hình thành công hệ thống cảnh báo chi tiêu với **AWS Budgets**:  
  - Cost Budget  
  - Usage Budget  
  - RI Budget  
  - Savings Plans Budget  
- Nắm bắt quy trình mở và theo dõi **Support Case** với đội ngũ AWS Support  

## Quản trị truy cập (IAM) & Hạ tầng mạng (VPC)
- Áp dụng nguyên tắc phân quyền tối thiểu thông qua **AWS IAM**  
- Xây dựng thành công hạ tầng mạng **Amazon VPC** từ đầu:  
  - Thiết lập Subnet, Internet Gateway, Route Table và các lớp Security Group  
  - Triển khai các máy chủ EC2 bên trong VPC  
  - Cấu hình **NAT Gateway** cho luồng dữ liệu đi ra và thiết lập kết nối **Site-to-Site VPN**  

## Vận hành EC2 & Triển khai ứng dụng
- Khởi chạy và kết nối thành công tới hai hệ điều hành **Microsoft Windows Server 2022** và **Amazon Linux 2**  
- Cài đặt hoàn chỉnh bộ môi trường web server **LAMP** trên Linux và **XAMPP** trên Windows  
- Triển khai thử nghiệm thành công ứng dụng **Node.js** trên EC2  
- Cấp quyền an toàn cho ứng dụng truy cập tài nguyên AWS bằng **IAM Roles**  
- Khởi tạo và quản lý dữ liệu cơ bản trên **Amazon S3 buckets**
