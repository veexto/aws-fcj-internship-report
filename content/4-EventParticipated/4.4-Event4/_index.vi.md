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

### Không khí sự kiện & Trải nghiệm tham gia
- **Phiên Q&A "không có hồi kết":** Sự kiện thu hút đông đảo các bạn sinh viên yêu thích Cloud và AI từ khắp các trường đại học tại TP. Hồ Chí Minh. Phần trao đổi hỏi đáp diễn ra cực kỳ sôi nổi với hàng loạt câu hỏi thực tế xoay quanh kinh nghiệm triển khai Bedrock Agent, bảo mật hệ thống cũng như lộ trình phát triển sự nghiệp Cloud Engineer.
- **Mini-game Quiz & Kết nối cộng đồng:** Không khí hội trường càng thêm hào hứng với phần trò chơi Quiz củng cố kiến thức cuối buổi. Ngoài ra, ban tổ chức cũng hé lộ thông tin về sự kiện lớn sắp diễn ra dành cho cộng đồng sinh viên: **AWS Student Community Day Vietnam 2026**.

---

### Bài học rút ra sau sự kiện
1. **Không dừng lại ở bản Demo:** Xây dựng AI Agent cho doanh nghiệp đòi hỏi phải thiết kế bài bản ngay từ đầu các lớp xác thực danh tính (Gateway/Identity), quản lý bộ nhớ dài hạn và cơ chế giám sát hành vi của mô hình.
2. **Tư duy kiến trúc tổng thể:** Hiểu rõ cách kết hợp **Amazon Bedrock AgentCore** với hạ tầng mạng VPC Multi-AZ của AWS để đảm bảo tính sẵn sàng cao và khả năng mở rộng cho hàng nghìn công cụ/tác vụ.
3. **Chủ động học hỏi từ cộng đồng:** Tích cực tham gia các buổi chia sẻ chuyên đề tại văn phòng AWS giúp cập nhật nhanh các dịch vụ mới nhất và mở rộng góc nhìn thực tế từ các anh/chị đi trước.
