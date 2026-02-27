---
description: Hướng dẫn tự động chạy Unit Test trước khi commit code
---
# Workflow: Chạy Auto-Test

1. Chạy `npm install` hoặc `mvn install` nếu có thư mục dependencies mới.
2. Thực thi `npm run test` hoặc `mvn test`.
3. Nếu phát hiện test pass 100%, mới cho phép thực hiện git commit.
4. Nếu thất bại, AI tự động quét lỗi của log test để phân tích nguyên nhân.
