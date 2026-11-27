---
title: "AWS Cloud and AI Day 2026 (Watch Party - TP. Hồ Chí Minh)"
date: 2026-09-29
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

### Thông tin chung về sự kiện
- **Tên sự kiện:** AWS Cloud and AI Day Hanoi 2026 – Điểm cầu Watch Party TP. Hồ Chí Minh
- **Thời gian:** Ngày 29/09/2026
- **Hình thức tham gia:** Tham gia trực tiếp tại điểm cầu **Watch Party TP. Hồ Chí Minh** (theo dõi trực tuyến các phiên Keynote & Developer Chats từ đầu cầu Hà Nội cùng cộng đồng AWS First Cloud Journey)
- **Đơn vị tổ chức:** AWS Việt Nam, AWS Community Builders & AWS First Cloud Journey (FCJ)

---

### Nội dung chính theo dõi từ sự kiện

#### 1. Chuyển dịch từ "Chấp nhận công nghệ" sang "Trưởng thành trong vận hành"
- Trọng tâm của cộng đồng Cloud và AI tại Việt Nam năm 2026 không còn dừng ở việc thử nghiệm Proof of Concept (PoC), mà đã bước sang giai đoạn **Operational Maturity** (đưa hệ thống lên môi trường production ổn định và an toàn).
- Một hệ thống production thực thụ đòi hỏi quyền sở hữu (ownership) rõ ràng, ranh giới truy cập chặt chẽ, khả năng giám sát toàn diện (observability), tính chịu lỗi cao (resilience) và mô hình quản trị chi phí có thể lặp lại ở quy mô lớn.

#### 2. Agentic AI và vai trò nền tảng của Platform Engineering
- **Agentic AI** là chủ đề xuyên suốt tại sự kiện: các AI Agent không chỉ dừng ở việc sinh văn bản mà đã trực tiếp gọi API, truy xuất dữ liệu nội bộ, chỉnh sửa mã nguồn và kích hoạt quy trình triển khai (deployment).
- Khi tốc độ phát triển và mức độ tự chủ của AI tăng lên, **Platform Engineering** đóng vai trò thiết yếu để thiết lập "lan can an toàn" (engineering guardrails): chuẩn hóa mẫu triển khai, thiết lập cấu hình bảo mật mặc định, kiểm soát chuỗi cung ứng phần mềm và quy trình phê duyệt hành động của Agent.

#### 3. Quản trị danh tính cho Workload & AI Agent (Workload Identity on AWS)
- Theo dõi phiên **Developer Chats** của diễn giả **Kha Văn** (Cloud Security Engineer / AWS Community Builder) xoay quanh câu hỏi cốt lõi: *"Khi một workload gọi AWS API, danh tính thực sự đang thực hiện yêu cầu đó là ai?"*
- Trong các hệ thống hiện đại, số lượng **danh tính phi con người (non-human identities)** như Kubernetes Pods, CI/CD pipelines, hàm Serverless và AI Agents vượt xa số lượng tài khoản người dùng thật.
- **Giải pháp thực tiễn trên AWS:** Áp dụng **Amazon EKS Pod Identity**, sử dụng thông tin xác thực tạm thời (temporary credentials), phân quyền chi tiết ở cấp độ từng workload thay vì kế thừa quyền rộng từ EC2 Node, kết hợp thiết kế Trust Policy chặt chẽ và xác minh tại thời điểm chạy (runtime verification).

#### 4. Mở rộng hạ tầng AWS tại Việt Nam & Bài toán kiến trúc Hybrid
- Sự kiện nhấn mạnh bước tiến hạ tầng của AWS tại Việt Nam với **AWS Direct Connect tại Hà Nội** và **AWS Local Zone tại Hà Nội**, mang lại thêm lựa chọn kết nối mạng riêng tư, độ trễ thấp (low-latency) và đáp ứng yêu cầu lưu trữ/xử lý dữ liệu tại chỗ (data locality).
- Điều này giúp các kiến trúc sư giải pháp linh hoạt hơn khi cân đối các yếu tố về độ trễ, tính tuân thủ, khả năng phục hồi và chi phí giữa hạ tầng tại chỗ (on-premises) với đám mây.

#### 5. Câu chuyện chuyển đổi thực tế & Sức mạnh cộng đồng Builder Việt Nam
- **Case study từ TCBS:** Cho thấy việc ứng dụng AI chỉ thực sự tạo ra bước ngoặt khi thay đổi cách đội ngũ kỹ sư viết, review, kiểm thử và bàn giao phần mềm, gắn liền với các chỉ số đo lường hiệu quả vận hành cụ thể.
- **Quy mô hệ sinh thái AWS tại Việt Nam:** Tính đến thời điểm diễn ra sự kiện, cộng đồng đã ghi nhận hơn **157.000** nhân sự được đào tạo về Cloud và AI, hơn **54.000** thành viên trên **AWS Study Group** và hơn **15.000** người tham gia hệ sinh thái **First Cloud and AI Journey (FCJ)**.

---

### Trải nghiệm tại Watch Party TP. Hồ Chí Minh & Bài học thu nhận
- **Không khí kết nối tại điểm cầu TP.HCM:** Dù sự kiện chính diễn ra tại Hà Nội, việc tham gia buổi Watch Party tại TP. Hồ Chí Minh giúp mình cùng các bạn thực tập sinh FCJ và mentor có không gian theo dõi trực tiếp, trao đổi ngay tại chỗ về các tình huống triển khai thực tế và mở rộng kết nối trong cộng đồng.
- **Ba bài học cốt lõi rút ra cho quá trình thực tập:**
  1. **Tư duy Production-First:** Khi xây dựng dự án trên AWS, luôn thiết kế đi kèm logging, giám sát và kiểm soát chi phí ngay từ đầu thay vì chỉ làm cho hệ thống chạy được ở mức demo.
  2. **Siết chặt bảo mật danh tính (Identity-Centric Security):** Tránh cấp quyền quá rộng cho dịch vụ hoặc AI Agent; ưu tiên cơ chế xác thực tạm thời và nguyên tắc đặc quyền tối thiểu (Least Privilege).
  3. **Tận dụng sức mạnh cộng đồng:** Chủ động học hỏi qua các buổi chia sẻ thực chiến của AWS Community Builders và chia sẻ lại kiến thức để củng cố tư duy kiến trúc hệ thống.
