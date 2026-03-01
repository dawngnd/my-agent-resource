---
description: Xử lý câu trả lời của user từ file conversation và tiếp tục thực hiện công việc
---

## Mô tả
Workflow này được kích hoạt khi user đã điền câu trả lời vào file conversation mới nhất trong thư mục `./conversation/`.

---

## Các bước thực hiện

### Bước 1: Tìm file conversation mới nhất
Đọc toàn bộ danh sách file trong thư mục `./conversation/`, lấy file có timestamp mới nhất (dựa vào tên file theo định dạng `YYYY-MM-DD_HH-mm_*.md`).

### Bước 2: Đọc và phân tích nội dung file
- Đọc file conversation mới nhất.
- Xác định các câu hỏi (Q1, Q2, ...) và trạng thái trả lời.
- Phân tích nội dung phần **Trả lời** của từng câu hỏi.

### Bước 3: Kiểm tra còn câu hỏi chưa trả lời không
- Nếu **còn câu hỏi chưa có trả lời** → Thông báo cho user và chờ.
- Nếu **tất cả đã được trả lời** → Tiếp tục Bước 4.

### Bước 4: Cập nhật trạng thái file conversation
- Đổi trạng thái trong file thành `ANSWERED`.
- Ghi chú ngắn tóm tắt những quyết định đã chốt.

### Bước 5: Thực thi các bước tiếp theo
Dựa vào nội dung câu trả lời, thực hiện các tác vụ tương ứng:
- Nếu là quyết định về thiết kế → Cập nhật tài liệu / sơ đồ.
- Nếu là quyết định về implementation → Bắt đầu viết code.
- Nếu cần thêm thông tin → Tạo file conversation mới theo quy trình trong `.agent/collaboration.md`.

### Bước 6: Kiểm tra còn câu hỏi phát sinh không
- Nếu **có câu hỏi mới** phát sinh trong quá trình thực thi → Tạo file conversation mới và thông báo cho user.
- Nếu **không còn câu hỏi nào** → Tiếp tục Bước 7.

### Bước 7: Đề xuất bước tiếp theo
Khi hoàn thành, trình bày cho user lựa chọn:

```
✅ Đã hoàn thành xử lý các câu trả lời.

Bạn muốn tiếp theo làm gì?

💬 [A] Tiếp tục trao đổi / thảo luận thêm về phase hiện tại
🚀 [B] Bắt đầu implement phase tiếp theo

→ Hãy trả lời A hoặc B (hoặc mô tả thêm yêu cầu).
```
