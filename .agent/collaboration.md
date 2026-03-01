---
description: Quy tắc cộng tác giữa Agent và User thông qua file conversation
---

# Quy tắc cộng tác (Collaboration Rules)

## Nguyên tắc giao tiếp

Khi làm việc trong workspace này, agent phải tuân theo quy trình sau:

### 1. Khi cần trao đổi / thắc mắc / cần review
- **KHÔNG** hỏi trực tiếp trong chat.
- Tạo một file `.md` mới trong thư mục **`./conversation/`** với tên theo định dạng:
  ```
  YYYY-MM-DD_HH-mm_<chủ-đề-ngắn-gọn>.md
  ```
  Ví dụ: `2026-02-26_15-30_database-design.md`
- File phải có cấu trúc chuẩn (xem mục 2).
- Sau khi tạo file, **thông báo** cho user biết đường dẫn file và chờ phản hồi.

### 2. Cấu trúc file conversation
```markdown
# [Chủ đề]

> Ngày tạo: YYYY-MM-DD HH:mm
> Trạng thái: PENDING | ANSWERED | DONE

---

## Bối cảnh
[Mô tả ngắn lý do tạo file này]

---

## Câu hỏi / Quyết định cần thiết

### Q1: [Câu hỏi 1]
**Gợi ý lựa chọn:**
- [ ] Option A: ...
- [ ] Option B: ...

> **Trả lời:** _(user điền vào đây)_

---

### Q2: [Câu hỏi 2]
...

> **Trả lời:** _(user điền vào đây)_

---

## Ghi chú thêm
_(user có thể bổ sung ở đây)_
```

### 3. Sau khi user trả lời
- Agent đọc file conversation mới nhất.
- Tiếp tục thực hiện các bước tiếp theo dựa trên câu trả lời.
- Cập nhật trạng thái file thành `ANSWERED` hoặc `DONE`.
- Nếu **không còn câu hỏi nào**, đề xuất user chọn:
  - 💬 **Tiếp tục trao đổi** (phase thảo luận thêm)
  - 🚀 **Bắt đầu implement**
