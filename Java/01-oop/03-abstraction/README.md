# 🌀 Tính trừu tượng (Abstraction)
**Abstraction(Trừu tượng)** là một trong bốn tính chất quan trọng của lập trình hướng đối tượng(OOP). Dùng để ẩn đi phần chi tiết bên trong (cách một đối tượng hoạt động) và chỉ cho người dùng thấy chức năng cần thiết.
Nó tập trung vào **“cái gì làm”** thay vì **“làm như thế nào”**.

**Các đặc điểm chính của Abstraction**

- **Ẩn chi tiết phức tạp** → Người dùng chỉ quan tâm đến chức năng, không cần biết logic bên trong.
-  Abstract class có thể **chứa phương thức chưa có phần thân** (abstract method), và bắt buộc các lớp con phải triển khai.
-  **Dễ bảo trì & linh hoạt** → Khi thay đổi cách triển khai bên trong, phần code bên ngoài sử dụng abstraction sẽ không bị ảnh hưởng.

**Ví dụ:** Giống như lái xe ô tô:

- Người lái chỉ cần biết đạp ga, phanh, vô lăng (chức năng cần thiết) mà không cần biết chi tiết động cơ hoạt động thế nào. 

→ Đây chính là **Abstraction**: tập trung vào cái cần dùng, giấu đi phần phức tạp.

---