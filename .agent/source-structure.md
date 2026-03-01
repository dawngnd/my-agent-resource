---
description: Quy tắc cấu trúc thư mục source code và vai trò quyền đọc/ghi của Agent
---

# Quy tắc cấu trúc Source Code

## Tổng quan

Toàn bộ source code của dự án được đặt trong thư mục **`./source/`** và chia thành 2 thư mục con với mục đích rõ ràng.

---

## Cấu trúc thư mục

```
source/
├── context/     # Source code do USER cung cấp (để agent hiểu nghiệp vụ)
├── generate/src    # Source code do AGENT viết ra
└── generate/test   # Test code do AGENT viết ra
```

---

## Chi tiết từng thư mục

### 📁 `source/context/`
- Chứa các file source code do **user cung cấp**.
- Mục đích: giúp agent hiểu **nghiệp vụ**, luồng xử lý, cấu trúc dữ liệu hiện có.
- Agent **chỉ đọc**, không được tự ý chỉnh sửa các file trong thư mục này.
- Có thể bao gồm: code hiện tại, code tham khảo, schema, API spec, v.v.

### 📁 `source/generate/`
- Chứa toàn bộ source code do **agent tạo ra**.
- Agent sẽ tạo, chỉnh sửa, xoá file trong thư mục này trong quá trình implement.
- Mọi file code được sinh ra đều phải tuân theo rule trong `java_rule.md` và `collaboration.md`.

---

## Quy tắc bắt buộc

| Hành động                        | `source/context/` | `source/generate/` |
|----------------------------------|:-----------------:|:------------------:|
| Agent đọc để hiểu nghiệp vụ      | ✅                | ✅                 |
| Agent tự tạo / sửa / xoá file    | ❌                | ✅                 |
| User cung cấp file tham khảo     | ✅                | ❌                 |
| Agent viết code mới              | ❌                | ✅                 |
