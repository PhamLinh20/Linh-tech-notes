# 🐣 Hướng Đối Tượng Trong Java (Object-Oriented Programming - OOP)

## 📌 Giới thiệu
OOP (Object-Oriented Programming) hay Lập trình Hướng Đối Tượng là phương pháp lập trình xoay quanh đối tượng (object).
Mỗi đối tượng sẽ gói gọn cả:
- Thuộc tính (Attributes / Fields): mô tả đặc điểm, trạng thái.
- Hành vi (Methods / Behaviors): mô tả những gì đối tượng có thể làm.

**Ví dụ :** Trong ứng dụng nghe nhạc có thể có các đối tượng sau : 

| Đối tượng | Thuộc tính | Hành vi |
|-----------|------------|----------|
| 🎵 **Bài hát** | • Tên bài hát <br> • Thời lượng <br> • Thể loại <br> • Ca sĩ <br> | • Phát nhạc <br> • Tạm dừng <br> • Dừng phát <br> • Tải về |
| 🎤 **Ca sĩ** | • Tên ca sĩ/ban nhạc <br> • Quốc tịch <br> • Danh sách bài hát <br> • Danh sách album | • Phát hành bài hát <br> • Phát hành album <br> • Hiển thị thông tin <br>  |
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



