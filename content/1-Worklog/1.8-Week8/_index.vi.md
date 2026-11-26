---
title: "Nhật ký công việc Tuần 8"
date: 2026-11-02
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---
### Mục tiêu Tuần 8:

- **Tối ưu hóa Chi phí (Cost Optimization):** Làm chủ các gói cam kết tiết kiệm chi phí như **Savings Plans** và **Reserved Instances (RI)** cho hệ thống EC2 và Amazon RDS.
- **Tối ưu hóa Quy mô Tài nguyên (Right Sizing):** Kết hợp **AWS Compute Optimizer** cùng CloudWatch Agent để đánh giá tải thực tế và điều chỉnh cấu hình instance phù hợp.
- **Quản trị Tài chính Đám mây (FinOps):** Khai thác **AWS Cost Explorer** để phân tích biến động chi tiêu theo dịch vụ và kiểm soát chi phí truyền tải dữ liệu (Data Transfer).
- **Đánh giá Năng lực Giữa kỳ:** Hoàn thành bài kiểm tra tổng hợp mô phỏng cấu trúc đề thi **AWS Certified Solutions Architect - Associate (SAA-C03)**.

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **Các Mô hình Cam kết Tiết kiệm Chi phí** <br> - Phân tích và so sánh cơ chế hoạt động giữa **Savings Plans** (Compute / EC2 Instance) và **Reserved Instances (RI)** <br> - Đánh giá bảng khuyến nghị **Recommendations** dựa trên lịch sử tiêu thụ tài nguyên <br> - Thực hành quy trình đăng ký gói Savings Plan và Reserved DB Instances cho RDS | 02/11/2026 | 02/11/2026 | https://000042.awsstudygroup.com/ |
| 3 | **Tối ưu hóa Tài nguyên & Right Sizing** <br> - Cài đặt và cấu hình **CloudWatch Agent** trên EC2 để thu thập chỉ số bộ nhớ (RAM) ngoài các chỉ số mặc định <br> - Thiết lập IAM Role cấp quyền thu thập dữ liệu cho CloudWatch và Compute Optimizer <br> - Sử dụng **AWS Compute Optimizer** để nhận diện các instance dư thừa cấu hình và chọn loại máy chủ tối ưu <br> - Áp dụng các nguyên tắc chuẩn (Best Practices) về tối ưu hiệu năng trên chi phí cho EC2 | 03/11/2026 | 03/11/2026 | https://000032.awsstudygroup.com/ |
| 4 | **Trực quan hóa & Phân tích Chi phí với Cost Explorer** <br> - Sử dụng **AWS Cost Explorer** để bóc tách chi phí theo từng Dịch vụ (Service) và Tài khoản (Account) <br> - Theo dõi tỷ lệ bao phủ (**Coverage**) và mức độ tận dụng (**Utilization**) của các gói Savings Plan / RI <br> - Đánh giá độ co giãn (**Elasticity**) của hạ tầng theo khung giờ cao điểm và thấp điểm | 04/11/2026 | 04/11/2026 | https://000034.awsstudygroup.com/ |
| 5 | **Phân tích Chi phí Nâng cao & Hệ thống hóa Kiến thức** <br> - Xây dựng các báo cáo tùy chỉnh (**Custom Reports**) chuyên biệt cho nhóm tài nguyên EC2 <br> - Phân tích chi tiết chi phí **Data Transfer** (liên vùng, liên AZ và đi ra Internet) <br> - *Nghiên cứu lý thuyết:* Tìm hiểu quy trình xuất **AWS Cost & Usage Report (CUR)** và truy vấn dữ liệu chi phí bằng **Amazon Athena** <br> - Tổng hợp lại toàn bộ kiến thức trọng tâm sau 8 tuần thực tập để chuẩn bị cho bài kiểm tra giữa kỳ | 05/11/2026 | 05/11/2026 | https://000034.awsstudygroup.com/ <br><br> _Ôn tập kiến thức SAA-C03_ |
| 6 | **Bài kiểm tra Đánh giá Giữa kỳ (Midterm Exam)** <br> - Thực hiện bài thi thử mô phỏng **AWS Certified Solutions Architect - Associate (SAA-C03)** <br> - Cấu trúc đề: 65 câu hỏi tình huống trắc nghiệm trong thời gian 130 phút <br> - Phạm vi kiến thức: IAM, VPC, EC2, S3, RDS, High Availability / Auto Scaling và Cost Optimization <br> - Chấm điểm, phân tích đáp án chi tiết và rà soát các mảng kiến thức cần củng cố | 06/11/2026 | 06/11/2026 | _Đề thi thử AWS SAA-C03 Practice Exam_ |

# Kết quả đạt được trong Tuần 8

## Chiến lược Tối ưu hóa Chi phí
- Phân biệt rõ ưu và nhược điểm giữa **Savings Plans** (linh hoạt theo mức cam kết giờ) và **Reserved Instances** (cố định theo cấu hình/AZ), từ đó lựa chọn phương án tối ưu cho từng bài toán vận hành.
- Thành thạo cách đọc hiểu công cụ **Recommendations** để xác định ngưỡng cam kết hợp lý mà không gây lãng phí ngân sách.
- Nắm vững quy trình áp dụng Reserved Instance cho **Amazon RDS** nhằm giảm đáng kể chi phí vận hành cơ sở dữ liệu dài hạn.

## Tối ưu hóa Quy mô Tài nguyên (Right Sizing)
- Triển khai thành công **CloudWatch Agent** để bổ sung chỉ số mức sử dụng RAM vào hệ thống giám sát, khắc phục giới hạn của các chỉ số hypervisor mặc định.
- Khai thác **AWS Compute Optimizer** để phát hiện chính xác các máy chủ đang cấp phát thừa tài nguyên (Over-provisioned) hoặc quá tải (Under-provisioned), làm cơ sở điều chỉnh kích thước (Right Sizing) hiệu quả.

## Quản trị Tài chính Đám mây (FinOps)
- Sử dụng thành thạo **AWS Cost Explorer** để theo dõi xu hướng chi tiêu theo ngày, tháng và phân bổ chi phí cho từng dịch vụ.
- Thiết lập được các **Custom Reports** giúp kiểm soát chặt chẽ chi phí **Data Transfer** — khoản mục thường phát sinh ngoài dự kiến trong các kiến trúc phân tán.
- Nắm rõ cách đánh giá hiệu quả đầu tư của các gói cam kết thông qua hai chỉ số cốt lõi là **Coverage** và **Utilization**.

## Đánh giá Tổng hợp Kiến thức (Midterm)
- Hoàn thành nghiêm túc bài kiểm tra mô phỏng chuẩn **AWS Certified Solutions Architect - Associate**.
- Hệ thống hóa vững chắc kiến thức nền tảng xoay quanh 4 trụ cột: **Compute, Storage, Networking và Database**.
- Khoanh vùng được các chủ đề chuyên sâu cần tập trung rèn luyện thêm trong giai đoạn nửa sau của kỳ thực tập (như kết nối Hybrid Cloud và kiến trúc mạng phức tạp).
