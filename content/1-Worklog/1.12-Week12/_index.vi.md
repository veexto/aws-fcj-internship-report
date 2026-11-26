---
title: "Nhật ký công việc Tuần 12"
date: 2026-11-30
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu Tuần 12:
- Nâng cấp trải nghiệm UI/UX tổng thể và chuẩn hóa kiến trúc quản lý state tập trung.
- Đồng bộ hóa các thành phần giao diện (frontend) với dữ liệu từ hệ thống backend theo thời gian thực.
- Siết chặt quy tắc kiểm tra dữ liệu (validation) và duy trì tính nhất quán của API contract.
- Đóng gói bộ thư viện UI component dùng chung như biểu mẫu (form), hộp thoại (modal) và thông báo trạng thái.
- Tối ưu hóa băng thông mạng, cơ chế bộ nhớ đệm (caching) nhằm hạn chế các lượt gọi API dư thừa.
- Hoàn thiện nền tảng kỹ thuật sẵn sàng cho các nghiệp vụ full-stack có độ tương tác cao.

---

### Kế hoạch công việc trong tuần:

| Ngày | Nội dung thực hiện | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
|-----|-----------|---------------|------------------|---------------------|
| 2 | - Thiết lập hệ thống quản lý state toàn cục (Redux / Zustand / Context API) <br>- Đồng bộ hóa trạng thái phiên làm việc (session) xuyên suốt ứng dụng | 30/11/2026 | 30/11/2026 | AWS Study Group |
| 3 | - Phát triển và chuẩn hóa bộ UI component tái sử dụng: trường nhập liệu (input), modal, hiệu ứng tải (loader) và thông báo phản hồi | 01/12/2026 | 01/12/2026 | AWS Study Group |
| 4 | - Kết nối luồng dữ liệu thực tế từ backend lên giao diện người dùng <br>- Bổ sung cơ chế tự động làm mới (auto-refresh) và cập nhật dữ liệu chủ động | 02/12/2026 | 02/12/2026 | AWS Study Group |
| 5 | - Siết chặt ràng buộc validation ở cả tầng API backend lẫn biểu mẫu frontend <br>- Rà soát và cố định cấu trúc phản hồi của API contract | 03/12/2026 | 03/12/2026 | AWS Study Group |
| 6 | - Tối ưu hóa hiệu năng hiển thị và lưu đệm dữ liệu phía client <br>- Áp dụng kỹ thuật memoization để loại bỏ các request gọi trùng lặp | 04/12/2026 | 04/12/2026 | AWS Study Group |

---

### Kết quả đạt được trong Tuần 12:

#### **1. Chuẩn hóa kiến trúc Global State Management**
Triển khai thành công mô hình quản lý state tập trung để đồng bộ phiên đăng nhập, trạng thái giao diện và luồng dữ liệu động. Cách tiếp cận này giúp cấu trúc mã nguồn gọn gàng hơn và loại bỏ tình trạng truyền props qua nhiều tầng trung gian (prop drilling).

#### **2. Đóng gói thư viện UI Component dùng chung**
Xây dựng hoàn chỉnh hệ thống component tiêu chuẩn bao gồm: button, input, modal, loader, skeleton và toast notification. Bộ thư viện này giúp giao diện giữ được sự đồng bộ về mặt thị giác, đồng thời rút ngắn đáng kể thời gian phát triển các tính năng mới.

#### **3. Đồng bộ dữ liệu Backend theo thời gian thực**
Kết nối thành công giao diện người dùng với nguồn dữ liệu thực từ hệ thống backend, đảm bảo trạng thái hiển thị luôn phản hồi tức thì theo từng thao tác. Hệ thống cũng được tích hợp song song hai chế độ làm mới tự động (auto-refresh) và làm mới thủ công theo nhu cầu.

#### **4. Siết chặt Validation và ổn định API Contract**
Hoàn thiện lớp kiểm tra tính hợp lệ của dữ liệu ở cả phía backend lẫn cấu hình mapping trên API Gateway. Kết hợp với cơ chế form validation chặt chẽ ở frontend, ứng dụng giảm thiểu tối đa lỗi nhập liệu từ người dùng và đảm bảo định dạng phản hồi API luôn nhất quán.

#### **5. Tối ưu hiệu năng và giảm tải lưu lượng API**
Áp dụng đồng bộ các kỹ thuật caching, memoization và khử trùng lặp request (request deduplication). Nhờ đó, tốc độ phản hồi của giao diện được cải thiện rõ rệt, giảm áp lực truy vấn lên hệ thống backend và tiết kiệm băng thông mạng.

#### **6. Sẵn sàng nền tảng cho các tính năng Full-stack nâng cao**
Hoàn tất toàn bộ hạ tầng giao diện và luồng xử lý dữ liệu cốt lõi, tạo tiền đề vững chắc để triển khai các nghiệp vụ full-stack phức tạp đòi hỏi cập nhật dữ liệu liên tục và tương tác động.

---
