---
title: "AWS Cloud Mastery: Xây dựng Amazon Bedrock Agent từ Prototype đến Production"
date: 2026-11-14
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

### Thông tin chung về sự kiện
- **Tên sự kiện:** AWS Cloud Mastery – Amazon Bedrock Agent: From Prototype to Production
- **Thời gian:** Sáng thứ Bảy, ngày 14/11/2026
- **Địa điểm:** Văn phòng AWS Việt Nam (TP. Hồ Chí Minh)
- **Diễn giả:** Anh Khang Duong (Thành viên AWS First Cloud Journey – FCJ)
- **Đơn vị tổ chức:** AWS First Cloud Journey (FCJ) & AWS Study Group

---

### Tổng quan buổi chia sẻ

Trong khuôn khổ chuỗi hoạt động nâng cao năng lực thực hành của cộng đồng **AWS First Cloud Journey (FCJ)**, buổi chuyên đề **AWS Cloud Mastery** tổ chức ngày 14/11/2026 tập trung giải quyết một bài toán thực tiễn của kỹ thuật AI hiện đại: thu hẹp khoảng cách từ giai đoạn thử nghiệm ý tưởng (*Prototype*) đến vận hành chính thức ở quy mô doanh nghiệp (*Production*).

Dưới sự dẫn dắt của diễn giả **Khang Duong** (thành viên FCJ), chương trình quy tụ đông đảo sinh viên công nghệ và các kỹ sư trẻ tại TP. Hồ Chí Minh đến trực tiếp không gian làm việc của AWS Việt Nam để cùng mổ xẻ kiến trúc **Amazon Bedrock AgentCore**. Thay vì dừng lại ở việc xây dựng các luồng hội thoại AI cơ bản, nội dung buổi học đi thẳng vào ba tiêu chuẩn bắt buộc của hệ thống thực tế: **Bảo mật (Secure), Độ tin cậy (Reliable) và Khả năng mở rộng (Scalable)**.

---

### Nội dung chuyên môn chính

#### 1. Thách thức khi đưa AI Agent từ Prototype lên Production
- Mở đầu phiên chia sẻ với chủ đề **"From Prototype to Production: Secure, Reliable, Scalable Enterprise AI on the Cloud"**, diễn giả chỉ ra khoảng cách lớn giữa việc chạy thử nghiệm một chatbot đơn giản và vận hành một **Enterprise AI Agent** thực thụ.
- **Ba thách thức cốt lõi của doanh nghiệp:**
  - **Hiệu năng & Chi phí:** Đảm bảo tốc độ phản hồi và tối ưu chi phí vận hành khi lượng truy cập tăng cao.
  - **Integration & Control:** Làm thế nào để AI Agent tương tác an toàn với các hệ thống nghiệp vụ thực tế mà không vượt quá phạm vi cho phép.
  - **Observability & Evaluation:** Làm sao giám sát được Agent đang thực hiện những bước nào và đánh giá chính xác chất lượng câu trả lời/hành động của Agent.

#### 2. Kiến trúc mở rộng quy mô với Amazon Bedrock AgentCore
- Để đáp ứng bài toán quy mô lớn (**100s Agents**, **1,000s Tools**, **100s MCP Servers** và **100k+ Tenants**), buổi chia sẻ đi sâu vào các thành phần cốt lõi của **Amazon Bedrock AgentCore**:
  - **Xác thực & Phân quyền đa lớp (Inbound & Outbound Auth):** Áp dụng khung xử lý 5 bước (*The universal 5-step skeleton*) thông qua **Bedrock AgentCore Gateway** và **AgentCore Identity**. Mọi yêu cầu gọi vào đều được xác thực danh tính (JWT hoặc IAM) trước khi Agent được cấp quyền kết nối tới các công cụ (Tools) và MCP Server bên ngoài.
  - **Quản lý ngữ cảnh thông minh với AgentCore Memory:**
    - **Short-term Memory:** Đồng bộ tức thì lịch sử hội thoại (*Chat Messages*) và trạng thái phiên (*Session State*).
    - **Long-term Memory:** Sử dụng *Automatic Memory Extraction Module* để trích xuất bất đồng bộ tri thức ngữ nghĩa (*Semantic*), sở thích người dùng (*User Preferences*), bản tóm tắt (*Summarization*) và kinh nghiệm xử lý tác vụ (*Episodic*).
  - **Kiến trúc hạ tầng AWS chuẩn Production:** Thiết kế triển khai trên nhiều Availability Zones (Multi-AZ) với sự phân tách rõ ràng giữa các tầng mạng công cộng/riêng tư, cân bằng tải, lớp điều phối Agent và hệ thống giám sát.

---

### Không khí trao đổi & Kết nối cộng đồng

- **Thảo luận chuyên sâu cùng người tham dự:** Phần tương tác trực tiếp tại hội trường diễn ra sôi nổi và kéo dài đến cuối chương trình với nhiều câu hỏi thực tế từ cộng đồng sinh viên công nghệ tại TP. Hồ Chí Minh. Các vấn đề được quan tâm xoay quanh cách kiểm soát phạm vi hành động của AI Agent khi tích hợp hệ thống nghiệp vụ thật, tối ưu chi phí vận hành và định hướng lộ trình theo đuổi mảng Cloud & AI.
- **Hệ thống hóa kiến thức qua trò chơi tương tác:** Khép lại phần trình bày kỹ thuật là hoạt động Quiz giúp củng cố nhanh các khái niệm cốt lõi về phân quyền Gateway, quản lý bộ nhớ ngắn/dài hạn và kiến trúc triển khai Multi-AZ trên AWS.
- **Mở rộng cơ hội tham gia cộng đồng:** Cuối buổi, ban tổ chức cũng chia sẻ thông tin về sự kiện quy mô lớn sắp tới dành cho giới sinh viên công nghệ — **AWS Student Community Day Vietnam 2026**, tạo thêm điểm hẹn học tập và kết nối cho các thành viên FCJ.

---

### Bài học rút ra sau sự kiện
1. **Không dừng lại ở bản Demo:** Xây dựng AI Agent cho doanh nghiệp đòi hỏi phải thiết kế bài bản ngay từ đầu các lớp xác thực danh tính (Gateway/Identity), quản lý bộ nhớ dài hạn và cơ chế giám sát hành vi của mô hình.
2. **Tư duy kiến trúc tổng thể:** Hiểu rõ cách kết hợp **Amazon Bedrock AgentCore** với hạ tầng mạng VPC Multi-AZ của AWS để đảm bảo tính sẵn sàng cao và khả năng mở rộng cho hàng nghìn công cụ/tác vụ.
3. **Chủ động học hỏi từ cộng đồng:** Tích cực tham gia các buổi chia sẻ chuyên đề tại văn phòng AWS giúp cập nhật nhanh các dịch vụ mới nhất và mở rộng góc nhìn thực tế từ các anh/chị đi trước.
