---
title: "Nhật ký công việc Tuần 5"
date: 2026-10-12
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---
### Mục tiêu Tuần 5:

- **Tối ưu Vận hành (Operational Excellence):** Tự động hóa các tác vụ vận hành định kỳ (bật/tắt máy chủ theo lịch) bằng **AWS Lambda** kết hợp thông báo qua công cụ cộng tác (Slack).
- **Giám sát & Trực quan hóa:** Xây dựng hệ thống dashboard chuyên sâu bằng **Grafana** kết nối trực tiếp với nguồn dữ liệu **Amazon CloudWatch**.
- **Quản trị & Phân loại Tài nguyên:** Chuẩn hóa chiến lược gắn nhãn (**Tagging**), tổ chức **Resource Groups** và áp dụng cơ chế kiểm soát truy cập dựa trên thuộc tính (**ABAC**) qua **AWS IAM**.
- **Quản trị Hệ thống (Systems Manager):** Thực hành truy cập máy chủ không cần mở cổng SSH bằng **Session Manager**, chạy lệnh hàng loạt với **Run Command** và tìm hiểu quy trình vá lỗi tự động (**Patch Manager**).
- **Hạ tầng dưới dạng Mã (IaC):** Bắt đầu tự động hóa việc khởi tạo tài nguyên đám mây thông qua **AWS CloudFormation**.

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| --- | --- | --- | --- | --- |
| 2 | **Tối ưu Chi phí & Tự động hóa Vận hành** <br> - Viết hàm **AWS Lambda** (Python `boto3`) tự động khởi động/tắt các EC2 instance theo khung giờ quy định <br> - Tích hợp Lambda với **Slack Incoming Webhooks** để gửi cảnh báo trạng thái vận hành tức thì <br> - Thiết lập lịch kích hoạt tự động bằng **Amazon EventBridge** (CloudWatch Events) | 12/10/2026 | 12/10/2026 | https://000022.awsstudygroup.com/ |
| 3 | **Giám sát Nâng cao với Grafana** <br> - Khởi chạy máy chủ EC2 để cài đặt và vận hành **Grafana** (Open Source) <br> - Kết nối Grafana với nguồn dữ liệu **Amazon CloudWatch** thông qua IAM Role <br> - Thiết kế dashboard trực quan hóa các chỉ số CPU, lưu lượng mạng và Disk I/O của EC2 | 13/10/2026 | 13/10/2026 | https://000029.awsstudygroup.com/ |
| 4 | **Quản trị Tài nguyên & Bảo mật (Tagging & IAM ABAC)** <br> - **Chiến lược Tagging:** Chuẩn hóa bộ thẻ phân loại cho tài nguyên (`Env`, `Owner`, `CostCenter`) <br> - Khởi tạo **Resource Groups** để gom nhóm và quản lý tập trung các tài nguyên cùng thuộc tính <br> - **Triển khai ABAC:** Viết IAM Policy cho phép người dùng chỉ thao tác được trên các EC2 có cặp thẻ trùng khớp với thẻ của chính họ | 14/10/2026 | 14/10/2026 | https://000027.awsstudygroup.com/ <br><br> https://000028.awsstudygroup.com/ |
| 5 | **Quản trị Hệ thống với AWS Systems Manager (SSM)** <br> - **Session Manager:** Truy cập an toàn vào EC2 (cả Public lẫn Private Subnet) mà không cần mở cổng SSH hay dùng Bastion Host; cấu hình Port Forwarding và lưu Session Logs lên S3 <br> - **Run Command:** Thực thi kịch bản quản trị từ xa đồng loạt trên nhiều máy chủ <br> - *Nghiên cứu lý thuyết:* Tìm hiểu quy trình rà soát và cập nhật bản vá tự động qua **Patch Manager** | 15/10/2026 | 15/10/2026 | https://000058.awsstudygroup.com/ <br><br> https://000031.awsstudygroup.com/ |
| 6 | **Hạ tầng dưới dạng Mã (AWS CloudFormation)** <br> - Biên soạn **CloudFormation Template** (YAML/JSON) để triển khai tự động VPC và EC2 <br> - Nắm vững cấu trúc các thành phần cốt lõi: **Stacks, Parameters, Mappings và Outputs** <br> - Thực hành tính năng **Drift Detection** để phát hiện các thay đổi cấu hình thủ công ngoài template | 16/10/2026 | 16/10/2026 | https://000037.awsstudygroup.com/ |

# Kết quả đạt được trong Tuần 5

## Tự động hóa & Tối ưu Chi phí
- Xây dựng thành công **cơ chế tiết kiệm chi phí tự động**, hẹn giờ tắt các máy chủ EC2 môi trường phát triển/kiểm thử ngoài giờ làm việc bằng **AWS Lambda**.
- Tích hợp luồng thông báo thời gian thực tới **kênh Slack** mỗi khi hệ thống thực thi tác vụ bật/tắt máy chủ, giúp đội ngũ dễ dàng theo dõi.
- Giảm thiểu thao tác thủ công lặp lại nhờ sử dụng **EventBridge Rules** làm bộ lập lịch kích hoạt tự động.

## Trực quan hóa Dữ liệu Giám sát
- Triển khai và vận hành thành công máy chủ **Grafana** tự quản trị trên nền tảng EC2.
- Tích hợp **Amazon CloudWatch** làm nguồn dữ liệu đầu vào, mở rộng khả năng biểu diễn chỉ số linh hoạt và trực quan hơn so với giao diện mặc định.
- Hoàn thiện bộ dashboard theo dõi sức khỏe hệ thống EC2 phục vụ công tác phân tích hiệu năng.

## Quản trị Tài nguyên & Phân quyền theo Thuộc tính
- Chuẩn hóa **quy tắc gắn thẻ (Tagging)** nhằm phân tách rõ ràng tài nguyên theo môi trường (`Dev`/`Prod`) và đơn vị sử dụng.
- Sử dụng **Resource Groups** để truy vấn và quản lý hàng loạt tài nguyên theo từng nhóm dự án.
- Nâng cao tính bảo mật nhờ mô hình **Attribute-Based Access Control (ABAC)**: thiết lập IAM Policy giới hạn quyền quản lý EC2 dựa trên sự trùng khớp thẻ giữa IAM User và tài nguyên, cô lập hiệu quả giữa các môi trường.

## Vận hành Hệ thống Tập trung (SysOps)
- Loại bỏ hoàn toàn rủi ro lộ cổng SSH và nhu cầu duy trì Bastion Host nhờ ứng dụng **SSM Session Manager**.
- Cấu hình lưu trữ **Session Logs** tự động lên Amazon S3 phục vụ công tác kiểm toán (audit) và tuân thủ bảo mật.
- Nắm vững quy trình vận hành **Patch Manager** để tự động hóa việc quét và cập nhật bản vá hệ điều hành định kỳ.
- Thành thạo **Run Command** để triển khai cấu hình đồng thời trên nhiều máy chủ mà không cần đăng nhập thủ công từng node.

## Hạ tầng dưới dạng Mã (Infrastructure as Code)
- Bước đầu chuyển dịch từ việc tạo tài nguyên thủ công trên Console sang khai báo bằng mã nguồn với **AWS CloudFormation**.
- Triển khai thành công CloudFormation Stack khởi tạo đồng bộ hạ tầng VPC và EC2 với tính nhất quán và khả năng tái sử dụng cao.
- Sử dụng thành thạo **Drift Detection** để kiểm tra và phát hiện sai lệch giữa trạng thái hạ tầng thực tế với cấu hình chuẩn trong template.
