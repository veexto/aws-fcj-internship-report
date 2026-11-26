---
title: "Fireside Chat with Dr. Werner Vogels: Navigating the Future of Cloud & AI in Vietnam"
date: 2026-10-02
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

### Thông tin chung về sự kiện
- **Tên sự kiện:** Fireside Chat with Dr. Werner: Navigating the Future of Cloud & AI in Vietnam
- **Diễn giả khách mời:** Tiến sĩ Werner Vogels (Vice President & Chief Technology Officer tại Amazon)
- **Thời gian:** Ngày 02/10/2026
- **Đơn vị tổ chức:** AWS First Cloud Journey (FCJ), AWS Heroes & AWS Community Builders Việt Nam

---

### Nội dung chính của buổi trò chuyện

#### 1. Lịch sử kiến trúc phân tán tại Amazon & Sự ra đời của DynamoDB
- **Từ bài toán thực tế đến dịch vụ đám mây cốt lõi:** Dr. Werner chia sẻ câu chuyện hơn 22 năm trước khi Amazon đối mặt với giới hạn của các hệ quản trị cơ sở dữ liệu quan hệ thương mại trong mùa cao điểm mua sắm. Qua quá trình phân tích tải thực tế, đội ngũ nhận ra phần lớn truy vấn (khoảng 70%) chỉ là thao tác **Key-Value** đơn giản — động lực trực tiếp dẫn đến việc tự xây dựng hệ thống **Dynamo** và sau này là **Amazon DynamoDB**.
- **Văn hóa tối ưu độ tin cậy (Operational Excellence):**
  - Tập trung đo lường và cải thiện độ trễ ở phân vị **p99.9** thay vì chỉ dựa vào giá trị trung bình.
  - Thực hành diễn tập **Game Days** — chủ động ngắt kết nối toàn bộ một trung tâm dữ liệu (Availability Zone) để loại bỏ các điểm lỗi đơn (Single Points of Failure), tự động hóa quy trình failover và hoàn thiện cơ chế đồng bộ dữ liệu khi hạ tầng phục hồi.
  - Thay đổi mô hình kinh tế ngành CNTT từ hợp đồng trả trước dài hạn sang **Pay-as-you-go**, trao quyền chủ động hoàn toàn cho khách hàng.

#### 2. Tư duy của "Renaissance Developer" trong kỷ nguyên AI
- **5 trụ cột năng lực của kỹ sư hiện đại:**
  1. **Curious (Học hỏi không ngừng):** Ngôn ngữ lập trình và công cụ luôn thay đổi (từ C/Java đến Rust, từ IDE truyền thống đến Kiro/Cursor); khả năng tự cập nhật tri thức là yếu tố sống còn.
  2. **Systems Thinker (Tư duy hệ thống):** Nhìn nhận bức tranh tổng thể về cách các dịch vụ tương tác thay vì chỉ tập trung vào một module rời rạc.
  3. **Communicative (Kỹ năng giao tiếp):** Là kỹ năng thường bị đánh giá thấp nhất nhưng lại quyết định hiệu quả công việc. Kỹ sư cần biết khai thác đúng bài toán nghiệp vụ của khách hàng và giải thích rõ sự đánh đổi chi phí (ví dụ: mức độ sẵn sàng 99,99% cho luồng thanh toán so với 99,9% cho tính năng gợi ý) thay vì lạm dụng GenAI cho mọi vấn đề.
  4. **Owner (Tinh thần làm chủ):** Công cụ AI chỉ là trợ lý; kỹ sư phải chịu trách nhiệm hoàn toàn về chất lượng mã nguồn, lỗ hổng bảo mật và tính tuân thủ của hệ thống đưa lên production.
  5. **Polymath (Kỹ sư chữ T):** Kết hợp chuyên môn sâu ở một lĩnh vực với kiến thức rộng ở các tầng liên quan (giao diện, nghiệp vụ, bảo mật/formal verification) trong mô hình nhóm nhỏ tinh gọn **Two-Pizza Teams** (10–12 người).

#### 3. Kết hợp AI Prototyping với quy trình "Working Backwards"
- **Đổi mới nhanh nhưng có kiểm soát:** Phương pháp **Working Backwards** (xây dựng tài liệu PR/FAQ từ góc nhìn khách hàng trước khi phát triển) nay được bổ trợ bởi tốc độ dựng prototype cực nhanh nhờ AI. Tuy nhiên, kỹ sư cần phân loại mức độ rủi ro của từng phần mềm để phân bổ thời gian review code hợp lý, tránh phụ thuộc mù quáng vào mã nguồn do AI sinh ra.
- **Khuếch đại giá trị con người:** Công nghệ suy cho cùng được tạo ra để phục vụ con người. Các công cụ AI nên được tận dụng để nâng cao những thế mạnh mà máy móc không thể thay thế: **khả năng phán đoán, tư duy sáng tạo, sự thấu cảm và niềm tự hào nghề nghiệp** đối với những hệ thống vận hành bền bỉ phía sau hậu trường.

---

### Bài học & Giá trị thu nhận sau sự kiện
1. **Chọn đúng công cụ cho đúng bài toán:** Không chạy theo trào lưu dùng mô hình AI lớn cho mọi tác vụ; luôn cân nhắc bài toán chi phí, độ trễ và độ tin cậy thực tế trước khi thiết kế kiến trúc.
2. **Đề cao trách nhiệm kỹ thuật (Engineering Ownership):** Khi ứng dụng các công cụ lập trình AI trong quá trình phát triển dự án, luôn chủ động kiểm thử, rà soát bảo mật và hiểu rõ từng dòng code triển khai.
3. **Rèn luyện kỹ năng giao tiếp kỹ thuật & tư duy hệ thống:** Biết cách trình bày giải pháp kiến trúc gắn liền với giá trị kinh doanh và chủ động kết nối, chia sẻ kiến thức cùng cộng đồng AWS First Cloud Journey.
