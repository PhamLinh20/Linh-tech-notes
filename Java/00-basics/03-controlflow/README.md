# 🧭Control Flow (Cấu trúc điều khiển trong Java)

Trong lập trình, control flow quyết định **thứ tự chương trình thực thi**.  
Nó cho phép bạn:
- **Ra quyết định** dựa trên điều kiện.
- **Lặp lại** các đoạn code nhiều lần.
- **Điều khiển hoặc dừng** luồng chạy khi cần thiết.

Hiểu control flow là nền tảng để viết chương trình **linh hoạt và dễ bảo trì**.

---

## 🎯Các loại cấu trúc điều khiển


| **Các loại cấu trúc điều khiển** | **Câu lệnh**     | **Mô tả** |
|----------------------------------|------------------|-----------|
| **Cấu trúc rẽ nhánh**           | `if-else`        | Thực hiện một khối lệnh khi **điều kiện đúng**, và chạy khối lệnh khác khi **điều kiện sai**. |
|                                  | `switch-case`    | Kiểm tra giá trị của biến và thực thi đoạn code tương ứng với **case** phù hợp. |
| **Cấu trúc lặp**                  | `for`            | Lặp lại đoạn code với **số lần đã biết trước**, thường dùng để duyệt qua một phạm vi giá trị. |
|                                  | `while`          | Lặp đoạn code **miễn là điều kiện còn đúng**, dừng lại khi điều kiện sai. |
|                                  | `do-while`       | Chạy đoạn code **ít nhất một lần**, sau đó kiểm tra điều kiện để quyết định lặp tiếp hay dừng. |
| **Câu lệnh nhảy**                 | `break`          | **Thoát khỏi vòng lặp hoặc `switch-case`** ngay lập tức và tiếp tục thực thi các câu lệnh bên ngoài. |
|                                  | `continue`       | Bỏ qua phần còn lại của vòng lặp hiện tại và tiếp tục với **lần lặp kế tiếp**. | 

---

## ⚡Cấu trúc rẽ nhánh
Dùng để **thực thi một khối lệnh dựa vào điều kiện đúng hoặc sai**.
### 1. `if`
Câu lệnh `if` được sử dụng để thực thi một khối lệnh khi điều kiện đúng.

**Cú pháp:**
```java
if (điều_kiện) {
    // code thực thi khi điều kiện đúng
} 
```
**Ví dụ:**
```java
if (score>=50) {
    System.out.println("Đạt yêu cầu");
} 
```
---
### 2. `if-else`
Câu lệnh `if-else` được sử dụng để thực thi một khối lệnh khi điều kiện đúng và khối lệnh khác nếu điều kiện là sai.

**Cú pháp:**
```java
if (điều_kiện) {
    // code khi điều kiện đúng
} else {
    // code khi điều kiện sai
}
```
**Ví dụ:**
```java
if (score>=50) {
    System.out.println("Đạt yêu cầu");
} else {
    System.out.println("Chưa đạt");
}
```
---
### 3. `if-else-if`
Câu lệnh `if-else-if` được sử dụng để thực thi một khối lệnh khi điều kiện đúng, khối lệnh khác nếu điều kiện là sai hoặc một khối lệnh mặc định khi tất cả điều kiện đều sai.

**Cú pháp:**
```java
if (điều_kiện_1) {
    // code khi điều kiện 1 đúng
} else if (điều_kiện_2) {
    // code khi điều kiện 2 đúng
} else {
    // code khi tất cả điều kiện đều sai
}
```
**Ví dụ:**
```java
if (age>=80) {
    System.out.println("Hoàn thành xuất sắc");
} else if(score>=50) {
    System.out.println("Đạt yêu cầu");
} else {
    System.out.println("Chưa đạt");
}
  
```
---
### 4. `switch-case`
Được dùng để chọn và chạy một khối lệnh trong nhiều lựa chọn, dựa vào giá trị của biểu thức.Thay vì dùng nhiều lệnh `if-else`, ta có thể dùng `switch-case` để chương trình chọn đúng khối lệnh cần thực thi theo giá trị đã cho.

**Cú pháp:**
```java
switch (biểu thức) {
    case giá trị 1:
        // code khi biểu thức == giá trị 1
        break;
    case giá trị 2:
        // code khi biểu thức == giá trị 2
        break;
    ...
    default:
        // code khi không khớp giá trị nào
}
```
**Ví dụ:**
```java
int day = 3;
switch (day) {
    case 1:
        System.out.println("Thứ Hai");
        break;
    case 2:
        System.out.println("Thứ Ba");
        break;
    case 3:
        System.out.println("Thứ Tư");
        break;
    default:
        System.out.println("Ngày không hợp lệ");
}
```
💡**Lưu ý** : Luôn dùng `break` để thoát khỏi `switch-case`, nếu không các case phía dưới sẽ tiếp tục thực thi.

---

## 🔁Cấu trúc lặp
### 1. `for`
Vòng lặp `for` giúp lặp đi lặp lại một khối lệnh với mỗi phần tử trong một tập hợp dữ liệu. Dùng khi biết trước số lần lặp .

**Cú pháp:**
```java
for (khởi tạo; điều kiện; cập nhật) {
    // code được lặp lại 
}
```
**Ví dụ:**
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```
---
### 2. `while`
Dùng để lặp đi lặp lại một khối lệnh miễn điều kiện đúng. Khác với `for`, `while` không biết trước số lần lặp nên sẽ chỉ dừng lại khi điều kiện sai.
**Cú pháp:**
```java
while (điều kiện) {
    // code lặp lại khi điều kiện đúng
}
``` 
**Ví dụ:**
```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```
---
### 3. `do-while`
Dùng để thực thi khối lệnh ít nhất một lần, sau đó lặp lại khối lệnh đó miễn điều kiện đúng.
**Cú pháp:**
```java
do {
    // code thực thi ít nhất 1 lần
} while (điều_kiện);
```
**Ví dụ:**
```java
int i = 0;
do {
    System.out.println(i);
    i++;
} while (i < 5);
```
---
## 🚀 Câu lệnh nhảy
Dùng để thay đổi luồng kiểm soát trong chương trình.
### 1. `break`
Câu lệnh `break` được dùng để thoát khỏi vòng lặp đột ngột khi gặp điều kiện nhất định, và chuyển sang thực thi câu lệnh ngay sau vòng lặp mà không cần duyệt hết các phần tử.

**Ví dụ:**
```java
for (int i = 0; i < 5; i++) {
    if (i == 3) {
        break; // dừng vòng lặp khi i = 3
    }
    System.out.println(i);
}
```
---
### 2. `continue`
Câu lệnh `continue` được dùng để bỏ qua lần lặp hiện tại của vòng lặp và tiếp tục với lần lặp tiếp theo. 

**Ví dụ:**
```java
for (int i = 0; i < 5; i++) {
    if (i == 2) {
        continue; // bỏ qua i = 2
    }
    System.out.println(i);
}
```
---
## ❗Lưu ý quan trọng
- `while` và `for` có thể không chạy lần nào nếu điều kiện ban đầu sai.
- `do-while` luôn chạy ít nhất một lần.
- Dùng `switch-case` khi có nhiều giá trị rẽ nhánh để mã gọn gàng và dễ đọc hơn.
- Tránh vòng lặp vô hạn bằng cách đảm bảo điều kiện vòng lặp có thể trở thành false.

**Ví dụ vòng lặp vô hạn:**
```java
int i = 0;
while (i < 5) {
    System.out.println("i = " + i);
    //Không cập nhật i(i++) => i luôn = 0 => điều kiện i < 5 luôn TRUE => vòng lặp chạy mãi
}
```
💥 **Kết quả**: Chương trình bị treo, không thể thoát.









