---
description: Quy trình sao chép và triển khai (copy & deploy) dựa trên cấu hình
---

Hãy thực hiện các bước sau để triển khai quy trình copy_deploy:

1. **Kiểm tra và khởi tạo cấu hình**:
   - Kiểm tra sự tồn tại của file `deploy/config.md` tại gốc dự án.
   - Nếu chưa có:
     - Tạo thư mục `deploy` nếu cần.
     - Tạo file `config.md` với Header: `| Source Folder | Destination Folder | Description |`.
     - Yêu cầu người dùng (USER) điền các đường dẫn cần thiết và dừng quy trình cho đến khi có phản hồi.

2. **Xác thực cấu hình**:
   - Đọc file `deploy/config.md`.
   - Kiểm tra xem các đường dẫn `Source Folder` có tồn tại trên hệ thống không.
   - Kiểm tra định dạng các đường dẫn để đảm bảo tính hợp lệ.

3. **Cập nhật cấu hình**:
   - Hỏi xác nhận từ USER: "Bạn có muốn cập nhật hoặc chỉnh sửa file `deploy/config.md` trước khi thực hiện copy không?"
   - Nếu USER muốn sửa, hãy đợi cho đến khi USER hoàn tất.

4. **Sao lưu (Backup)**:
   - Trước khi copy, với mỗi thư mục đích (Destination Folder) đã tồn tại:
     - Lấy thời gian hiện tại theo định dạng `yyyyMMddHHmmss`.
     - Tạo thư mục backup có tên `backup_[timestamp]` cùng cấp hoặc bên trong thư mục đích (tùy thuộc vào tính an toàn của cấu trúc).
     - Lưu trữ nội dung cũ của thư mục đích vào thư mục backup này.

5. **Thực hiện Copy**:
   - Tiến hành copy toàn bộ nội dung từ `Source Folder` sang `Destination Folder`.
   - Đảm bảo giữ nguyên cấu trúc thư mục con.

6. **Báo cáo kết quả**:
   - Tạo (hoặc ghi đè) file `deploy/result.md`.
   - Liệt kê chi tiết danh sách tất cả các file đã được sao chép thành công.
   - Hiển thị thông báo hoàn tất và đường dẫn tới file `result.md` cho USER.
