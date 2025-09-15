# ➕ Operators trong Java

Toán tử (**Operator**) là các ký hiệu đặc biệt dùng để thực hiện phép toán trên biến và giá trị.  
Java hỗ trợ nhiều loại toán tử từ cơ bản đến nâng cao.  

---

## 🧩 Các nhóm toán tử chính

### 1. **Arithmetic Operators (Toán tử số học)**
Dùng để tính toán các giá trị số học.

| Toán tử | Ý nghĩa      | Ví dụ (`a = 10`, `b = 3`) | Kết quả |
|---------|--------------|----------------------------|---------|
| `+`     | Cộng         | `a + b`                    | 13      |
| `-`     | Trừ          | `a - b`                    | 7       |
| `*`     | Nhân         | `a * b`                    | 30      |
| `/`     | Chia lấy phần nguyên | `a / b`            | 3       |
| `%`     | Chia lấy dư  | `a % b`                    | 1       |

💡 **Lưu ý:**  
- Nếu một toán hạng là số thực (`float` hoặc `double`), kết quả sẽ là số thực.
- Khi chia cho `0` với số nguyên sẽ **throw `ArithmeticException`**.

---

### 2. **Assignment Operators (Toán tử gán)**
Dùng để gán hoặc cập nhật giá trị cho biến.

| Toán tử | Ý nghĩa                 | Ví dụ (`x = 5`) | Kết quả |
|---------|------------------------|----------------|---------|
| `=`     | Gán                     | `x = 10`       | 10      |
| `+=`    | Cộng rồi gán            | `x += 3`       | 8       |
| `-=`    | Trừ rồi gán             | `x -= 2`       | 3       |
| `*=`    | Nhân rồi gán            | `x *= 2`       | 10      |
| `/=`    | Chia rồi gán            | `x /= 2`       | 5       |

---

### 3. **Comparison Operators (Toán tử so sánh)**
Dùng để so sánh hai giá trị, trả về `true` hoặc `false`.

| Toán tử | Ý nghĩa | Ví dụ (`a = 10`, `b = 3`) | Kết quả |
|---------|---------|---------------------------|---------|
| `==`    | Bằng nhau | `a == b`                | false   |
| `!=`    | Khác nhau | `a != b`                | true    |
| `>`     | Lớn hơn | `a > b`                   | true    |
| `<`     | Nhỏ hơn | `a < b`                   | false   |
| `>=`    | Lớn hơn hoặc bằng | `a >= b`       | true    |
| `<=`    | Nhỏ hơn hoặc bằng | `a <= b`       | false   |

---

### 4. **Logical Operators (Toán tử logic)**
Dùng để kết hợp các điều kiện boolean.

| Toán tử | Ý nghĩa        | Ví dụ (`x = true`, `y = false`) | Kết quả |
|---------|----------------|---------------------------------|---------|
| `&&`    | AND (và)       | `x && y`                        | false   |
| `\|\|`  | OR (hoặc)      | `x \|\| y`                       | true    |
| `!`     | NOT (phủ định) | `!x`                            | false   |

💡 **Lưu ý:**  
Trong Java, hai toán tử && (AND) và || (OR) hoạt động theo cơ chế ngắn mạch (short-circuit evaluation).
Điều này có nghĩa là nếu kết quả của biểu thức đã được xác định ở vế trái, Java sẽ không cần kiểm tra vế phải nữa, giúp tối ưu hiệu năng và tránh lỗi không mong muốn.

---

### 5. **Unary Operators (Toán tử một ngôi)**
Dùng cho **một biến duy nhất**.

| Toán tử | Ý nghĩa | Ví dụ (`a = 5`) | Kết quả |
|---------|---------|-----------------|---------|
| `++`    | Tăng 1 (prefix hoặc postfix) | `++a` hoặc `a++` | 6 |
| `--`    | Giảm 1 (prefix hoặc postfix) | `--a` hoặc `a--` | 4 |
| `+`     | Dương (giữ nguyên giá trị) | `+a` | 5 |
| `-`     | Đảo dấu | `-a` | -5 |

---

### 6. **Ternary Operator (Toán tử ba ngôi)**
- Toán tử ternary (toán tử ba ngôi) trong Java là một cách viết rút gọn của câu lệnh if-else, giúp code ngắn gọn và dễ đọc hơn khi cần gán giá trị hoặc xử lý điều kiện đơn giản.:
- Cú pháp: 
```java
result = condition ? valueIfTrue : valueIfFalse;
```
- Ví dụ: 
```java
String result = (age >= 18) ? "Adult" : "Child";
```
---

### 7. **instanceof**
Kiểm tra xem một object có thuộc kiểu dữ liệu nào đó hay không:
```java
String s = "Hello";
System.out.println(s instanceof String); // true
```
---
## 🧩 Các câu hỏi thường gặp

### 1. Phân biệt `++a` và `a++`
| Toán tử | Ý nghĩa |
|---------|----------|
| `++a` (**prefix**) | Tăng **trước**, sau đó trả về **giá trị mới** |
| `a++` (**postfix**) | **Trả về giá trị cũ** trước, rồi mới tăng |

**Ví dụ:**
```java
int a = 5;

System.out.println(++a); // 6 → a tăng trước, sau đó in ra 6
System.out.println(a++); // 6 → in ra giá trị cũ, rồi a tăng lên 7
System.out.println(a);   // 7
```
---

### 2. Sự khác nhau giữa `&&` và `&`
| Toán tử | Ý nghĩa |
|---------|----------|
| `&&` | short-circuit, nếu vế trái đã xác định kết quả → bỏ qua vế phải|
| `&`  | luôn kiểm tra cả hai vế, dễ gây lỗi hoặc kém tối ưu|

**Ví dụ**
```java
int a = 5;

// Dùng && → an toàn, không lỗi
if (a > 10 && (a / 0 == 1)) {
    System.out.println("Valid");
} else {
    System.out.println("Safe check"); // In ra dòng này
}

// Dùng & → luôn kiểm tra cả hai vế → gây lỗi ArithmeticException
if (a > 10 & (a / 0 == 1)) {
    System.out.println("This will crash");
}
```
---
### 3. Phân biệt `==` và `.equals()`
| Toán tử | Ý nghĩa |
|---------|----------|
| `==` | So sánh tham chiếu bộ nhớ (cùng object không) |
|`.equals()`  | So sánh nội dung giá trị của object|

**Ví dụ**
```java
String s1 = new String("Hello");
String s2 = new String("Hello");

System.out.println(s1 == s2);      // false → khác vùng nhớ
System.out.println(s1.equals(s2)); // true → cùng nội dung
```


