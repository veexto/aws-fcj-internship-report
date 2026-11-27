---
title: "First Cloud AI Journey: Weekly Meet Up 24/10"
date: 2026-10-24
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Thông tin chung về sự kiện
- **Tên sự kiện:** First Cloud AI Journey: Weekly Meet Up 24/10
- **Thời gian:** Ngày 24/10/2026
- **Đơn vị tổ chức:** AWS First Cloud Journey (FCJ) & AWS Study Group

---

### Nội dung các phiên chia sẻ chuyên sâu

#### 1. Xây dựng hệ thống Voice AI Agent & Phỏng vấn tự động
- **Diễn giả:** Anh Kiệt Trần (Engineer tại Revve AI – AWS Partner)
- **Nội dung chính:**
  - Phân tích bài toán độ trễ trong giao tiếp giọng nói tự nhiên (~200ms) và so sánh 3 kiến trúc xây dựng Voice AI: **Cascaded** (ASR → LLM → TTS), **Speech-to-Speech** và **Full Speech-to-Speech** kết hợp mô hình suy luận chạy ngầm.
  - Tìm hiểu luồng xử lý cuộc gọi thực tế qua SIP Server, Media Server (WebRTC/UDP), lọc nhiễu (Noise Canceller) và nhận diện điểm ngắt câu (VAD) giúp đạt tổng độ trễ phản hồi ~1,8 giây trên hạ tầng GPU Multi-AZ kết nối qua AWS PrivateLink.
  - Theo dõi phần **Live Demo** nền tảng trợ lý tuyển dụng AI gọi điện phỏng vấn trực tiếp ứng viên về kiến thức AWS (EC2, S3, EKS, RDS, VPC), kèm bài học thực tế về chuẩn hóa đọc văn bản tiếng Việt cho TTS, lớp kiểm duyệt Guardrails và tối ưu chi phí vận hành (~3.000đ/cuộc gọi).

#### 2. Quản lý và chia sẻ tài nguyên đa tài khoản với AWS Resource Access Manager (AWS RAM)
- **Diễn giả:** Anh Long (AWS Study Group)
- **Nội dung chính:**
  - Giải quyết bài toán quản trị hạ tầng phân mảnh trong môi trường **Multi-Account** bằng cách chia sẻ tập trung hơn 40 loại tài nguyên (VPC Subnets, Security Groups, Reserved EC2 Instances...) thông qua **AWS RAM** mà không phát sinh phí chia sẻ.
  - Nắm vững cơ chế kết hợp quyền hạn giữa AWS RAM Permissions, IAM Policy và Service Control Policies (SCP) của AWS Organizations, kết hợp giám sát qua EventBridge và CloudTrail.
  - Lưu ý kỹ thuật khi triển khai bằng Terraform/CloudFormation: đồng bộ **Availability Zone ID (AZ ID)** giữa các tài khoản để tránh phát sinh cước truyền dữ liệu liên vùng và ứng dụng mô hình mạng Hub-and-Spoke.

#### 3. Kiểm thử bảo mật tự động với AWS Security Agent
- **Diễn giả:** Anh Thịnh (Engineer tại Steel Solution)
- **Nội dung chính:**
  - Khám phá 3 năng lực cốt lõi của **AWS Security Agent**: **Design Review** (đánh giá mã hạ tầng Terraform để phát hiện rủi ro kiến trúc sớm), **Code & Security Review** (tích hợp thẳng vào GitHub/GitLab Pull Request và CI/CD) và **Automated Penetration Testing** (giả lập hành vi người dùng thật để lập đồ thị tấn công và dò tìm lỗ hổng trên môi trường SIT/UAT).
  - Thảo luận chuyên sâu về mô hình chia sẻ trách nhiệm (Shared Responsibility Model) và phương án dùng agent/extension kết nối qua đường hầm riêng tư tới máy chủ GitLab tự lưu trữ (self-hosted) để bảo vệ mã nguồn.

#### 4. Đưa AI Agent lên Production với Amazon Bedrock AgentCore
- **Diễn giả:** Anh Nguyễn Sơn An (Leader AWS Student Group tại HCMUTE)
- **Nội dung chính:**
  - Phân tích các thách thức về bảo mật, cô lập phiên và quản lý trạng thái khi đưa AI Agent từ môi trường thử nghiệm lên hệ thống vận hành thực tế.
  - Tìm hiểu kiến trúc **Amazon Bedrock AgentCore** với hai trụ cột chính:
    - **Runtime:** Môi trường serverless chạy mỗi phiên trên một **MicroVM** độc lập (EC2 Spot Instance), tối ưu chi phí khi chỉ tính phí CPU lúc thực thi.
    - **Memory:** Tách biệt giữa **Short-term Memory** (lưu hội thoại đồng bộ theo `sessionId` hỗ trợ phân nhánh) và **Long-term Memory** (tự động trích xuất bất đồng bộ tóm tắt, sở thích cá nhân và tri thức dài hạn).

#### 5. Tối ưu quy trình phát triển & vận hành tự động 24/7 với Kiro
- **Diễn giả:** Anh Hiếu Nghị (Leader AWS Student Group) & Anh Khoa (Tech Lead tại ACB)
- **Nội dung chính:**
  - Tiếp cận phương pháp **Spec-Driven Development** (Plan → Design → Tasks) cùng các lớp bảo vệ an toàn (tự động che giấu secrets/passwords, yêu cầu phê duyệt thủ công trước các lệnh xóa hạ tầng).
  - Tham khảo mô hình triển khai thực tế tại doanh nghiệp: kết nối Kiro với **Telegram** để giám sát tài nguyên AWS định kỳ mỗi 5 phút, tự động hóa quy trình **Code Review** trên GitHub theo bộ tiêu chuẩn nội bộ, và kiểm soát Context Window để tối ưu chi phí token.

---

### Bài học & Giá trị thu nhận sau sự kiện
1. **Tư duy kiến trúc thực chiến:** Hiểu rõ sự đánh đổi giữa độ trễ, độ chính xác ngôn ngữ và chi phí khi thiết kế các hệ thống GenAI/Voice AI và hạ tầng Multi-Account trên AWS.
2. **Nâng cao nhận thức về DevSecOps:** Biết cách áp dụng kiểm thử bảo mật tự động ngay từ giai đoạn thiết kế hạ tầng (IaC) và Pull Request thay vì đợi đến khi triển khai xong mới rà soát.
3. **Cập nhật công cụ Agentic mới nhất của AWS:** Nắm bắt cách vận hành AI Agent ở quy mô production với Amazon Bedrock AgentCore và ứng dụng Kiro để tăng tốc độ phát triển phần mềm trong dự án thực tập.


![Ảnh tham gia](AWSevent3(1).jpg)
![Ảnh tham gia](AWSevent3(2).jpg)
![Ảnh tham gia](AWSevent3(3).jpg)
![Ảnh tham gia](AWSevent3(4).jpg)
![Ảnh tham gia](AWSevent3(5).jpg)
![Ảnh tham gia](AWSevent3(6).jpg)

