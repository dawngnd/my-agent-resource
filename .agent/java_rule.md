---
description: Quy tắc phát triển Java, coding convention và các chuẩn mực cho dự án FacePay
---

# Workspace Rules – FacePay Project

## 1. Java Version
- Sử dụng **JDK 17** (LTS).

---

## 2. Framework
- Sử dụng **Spring Boot 3.x** (phiên bản mới nhất trong dòng 3).
- Spring Boot 3 yêu cầu tối thiểu **Jakarta EE 9** — sử dụng namespace `jakarta.*` thay cho `javax.*`.
---

## 3. Coding Convention – Oracle Java Code Conventions
Tuân thủ theo chuẩn Oracle Java Code Conventions (https://www.oracle.com/java/technologies/javase/codeconventions-introduction.html).

### 3.1. Đặt tên (Naming Conventions)
| Thành phần       | Quy tắc                                   | Ví dụ                    |
|------------------|-------------------------------------------|--------------------------|
| Package          | Chữ thường, viết liền, dùng dấu chấm     | `com.facepay.service`    |
| Class / Interface| UpperCamelCase (PascalCase)               | `PaymentService`         |
| Method           | lowerCamelCase, bắt đầu bằng động từ      | `processPayment()`       |
| Variable         | lowerCamelCase                            | `accountBalance`         |
| Constant         | UPPER_SNAKE_CASE (`static final`)         | `MAX_RETRY_COUNT`        |
| Enum             | UpperCamelCase; giá trị là UPPER_SNAKE    | `PaymentStatus.SUCCESS`  |

### 3.2. Định dạng code
- **Indentation**: 4 spaces (không dùng tab).
- **Độ dài dòng tối đa**: 100 ký tự.
- **Dấu ngoặc nhọn `{}`**: luôn mở ngoặc trên cùng dòng (K&R style).
  ```java
  if (condition) {
      doSomething();
  } else {
      doOther();
  }
  ```
- Mỗi câu lệnh trên 1 dòng riêng.
- Có 1 dòng trống giữa các method.

### 3.3. Tổ chức file
- Thứ tự trong class:
  1. Biến `static final` (constants)
  2. Biến instance (fields)
  3. Constructor(s)
  4. Public methods
  5. Protected methods
  6. Private methods
- Mỗi file chỉ chứa 1 public class/interface.

### 3.4. Javadoc & Comments
- Mọi public class, public/protected method phải có **Javadoc**.
- Sử dụng `//` cho comment nội dòng, tránh comment thừa/không có giá trị.
- Không để code được comment-out trong source chính thức (dùng Git thay thế).
  ```java
  /**
   * Processes a payment transaction.
   *
   * @param request the payment request details
   * @return the payment response
   */
  public PaymentResponse processPayment(PaymentRequest request) { ... }
  ```

### 3.5. Các quy tắc khác
- Sử dụng **generics** đúng cách, tránh raw type.
- Sử dụng **Optional** thay vì trả về `null` khi phù hợp.
- Viết **unit test** (JUnit 5) cho mọi business logic quan trọng.
  - **🚨 QUY TẮC BẮT BUỘC:** Mỗi khi chỉnh sửa, cập nhật hoặc tái cấu trúc (refactor) source code, LUÔN LUÔN phải kiểm tra và cập nhật/viết lại các file Unit Test tương ứng bị ảnh hưởng. Không bao giờ được bỏ qua bước này.
- Tuân thủ nguyên tắc **SOLID**.

