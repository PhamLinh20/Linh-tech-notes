# 🐣 Hướng Đối Tượng Trong Java (Object-Oriented Programming - OOP)

## 📌 Giới thiệu
**Lập trình hướng đối tượng (OOP - Object-Oriented Programming)** là một phương pháp lập trình dựa trên **đối tượng** – nơi mà **dữ liệu (thuộc tính)** và **hành vi (phương thức)** được gói gọn trong cùng một thực thể.  

Trong Java, OOP là **cốt lõi của ngôn ngữ**. Việc nắm vững OOP là nền tảng để bạn có thể phát triển các **ứng dụng thực tế**, từ những dự án nhỏ đến hệ thống phần mềm phức tạp.

---

## 🧩 4 tính chất cơ bản của OOP

### 1. **Encapsulation** – Tính đóng gói
> Giấu thông tin bên trong đối tượng và chỉ cung cấp những gì cần thiết để sử dụng.

- Sử dụng **Access Modifiers** (`private`, `public`, `protected`, `default`) để kiểm soát phạm vi truy cập.  
- Dữ liệu được bảo vệ thông qua **getter** và **setter**.

---

### 2. **Inheritance** – Tính kế thừa
> Cho phép một lớp **kế thừa** thuộc tính và phương thức của lớp khác.

- Giúp **tái sử dụng code**, giảm trùng lặp.  
- Trong Java, **chỉ hỗ trợ kế thừa đơn** (một lớp con chỉ có một lớp cha).
- Bao gồm **`super-keyword`** để gọi constructor, phương thức hoặc biến từ lớp cha.

---

### 3. **Polymorphism** – Tính đa hình
> Một đối tượng có thể **thể hiện nhiều hình thái khác nhau**.

- **Compile-time Polymorphism (Overloading):** Cùng tên phương thức nhưng **khác tham số**.
- **Runtime Polymorphism (Overriding):** Ghi đè phương thức ở lớp con để thay đổi hành vi.

---

### 4. **Abstraction** – Tính trừu tượng
> Chỉ tập trung vào **cái gì** đối tượng làm, không quan tâm **nó làm như thế nào**.

- **Abstract class**: Chứa phương thức trừu tượng và phương thức thông thường.  
- **Interface**: Chỉ định các hành vi, hỗ trợ **đa kế thừa**.



