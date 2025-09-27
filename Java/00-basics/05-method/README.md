# ⚙️ Phương thức (Method)
Trong lập trình **Java**, **method (hàm/phương thức)** là **tập hợp các câu lệnh** được định nghĩa để **thực hiện một chức năng cụ thể**. 

Việc sử dụng method giúp:
- **Tái sử dụng code** nhiều lần.
- **Tổ chức chương trình gọn gàng**, dễ quản lý.
- Giảm lặp code, dễ bảo trì và nâng cấp.
- **Hiểu đơn giản:**   Method trong Java **giống như một "công cụ"**: bạn đưa dữ liệu vào → xử lý → nhận kết quả đầu ra.

**Ví dụ:**
Trong hệ thống bán hàng online, mỗi hành động của người dùng hoặc hệ thống đều có thể được coi là phương thức:

- **Thêm sản phẩm vào giỏ hàng (addToCart)**: Khi khách chọn mua một sản phẩm, phương thức này sẽ thêm sản phẩm đó vào giỏ.
- **Thanh toán (checkout)**: Xử lý đơn hàng, tính tổng tiền và tiến hành thanh toán.
- **Tính tổng tiền giỏ hàng (calculateTotal)**: Cộng dồn giá của tất cả sản phẩm trong giỏ.

---
## ⚡ Các thao tác cơ bản với method
### 1. Khai báo method
- **Cú pháp:**
```java
modifier returnType methodName(parameters) {
    // Nội dung xử lý
    return value; // nếu returnType khác void
}
```
Ý nghĩa các thành phần:

- `modifier`: Phạm vi truy cập (public, private, protected, default).
- `returnType`: Kiểu dữ liệu trả về (int, String, void...).
- `methodName`: Tên hàm (đặt theo quy tắc camelCase).
- `parameters`: Danh sách tham số (có thể có hoặc không).
- `return` : Giá trị trả về (nếu không trả về → dùng void).

**Ví dụ:**
```java
public int add(int a, int b) {
    return a + b;
}
```
---
### 2. Gọi method
- Thực thi phương thức đã khai báo.
- **Ví dụ:**
```java
int result = add(5, 3); // truyền đối số (arguments) vào phương thức.
System.out.println(result); // 8
```

---
### 3. `static` method
- static dùng để khai báo method thuộc class, không thuộc đối tượng cụ thể.
- Có thể gọi trực tiếp bằng tên class, không cần tạo object.
- Thường dùng cho:
  - Hàm tiện ích (Math.sqrt(), Collections.sort()).
  - Hằng số, logic không phụ thuộc vào trạng thái của đối tượng.

**Ví dụ:**
```java
public class Utils {
    static int square(int x) {
        return x * x;
    }
}
public class Main {
    public static void main(String[] args) {
        int result = Utils.square(5); // Gọi trực tiếp mà không cần tạo object
        System.out.println(result);   // 25
    }
}
```
💡 **Lưu ý:** `static` method không thể truy cập trực tiếp biến instance hoặc method non-static.
- `static` method thuộc về class, không gắn với object nào.
- `Instance (non-static) method/biến`  gắn với object cụ thể.

Vì `static` không có object đi kèm, nên nó không biết phải lấy dữ liệu từ object nào → không thể truy cập trực tiếp biến `instance` hay `method non-static`.

- Ví dụ trong ngân hàng:
   - `static` : lãi suất chung của cả ngân hàng → ai cũng xem được, không cần tài khoản.
   - `Instance` : số dư tài khoản → phải có tài khoản cụ thể thì mới biết số dư.

---
### 4. Method Overloading (Nạp chồng phương thức)
- Overloading là cơ chế cho phép hai hoặc nhiều phương thức có cùng tên nhưng:
  - Khác danh sách tham số (số lượng, kiểu dữ liệu hoặc thứ tự tham số).
  - Có thể cùng hoặc khác kiểu trả về.

- Lợi ích:
  - Giúp code dễ đọc, trực quan hơn.
  - Hỗ trợ các tình huống giống nhau nhưng dữ liệu đầu vào khác nhau.

**Ví dụ:**
```java
public class Calculator {
    // Cộng 2 số nguyên
    int add(int a, int b) {
        return a + b;
    }

    // Cộng 3 số nguyên
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Cộng 2 số thực
    double add(double a, double b) {
        return a + b;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator cal = new Calculator();
        System.out.println(cal.add(2, 3));        // 5
        System.out.println(cal.add(2, 3, 4));     // 9
        System.out.println(cal.add(2.5, 3.5));    // 6.0
    }
}
```
💡**Lưu ý:** `Overloading` chỉ xét tham số, không xét kiểu trả về.

- Khi gọi method, Java dựa vào tên + tham số để quyết định gọi method nào.
Kiểu trả về chỉ dùng sau khi method chạy xong, không giúp phân biệt lúc compile.

**Ví dụ:**
```java
class Calculator {
    // Hợp lệ: khác tham số
    int add(int a, int b) {
        return a + b;
    }

    double add(double a, double b) {
        return a + b;
    }

    // ❌ Lỗi: chỉ khác kiểu trả về, tham số giống nhau
    int add(int a) {
        return a;
    }

    double add(int a) { // Compiler không biết gọi cái nào
        return a;
    }
}
```
- Nếu chỉ khác kiểu trả về thì khi ta gọi add(5); Java không biết nên chọn int add(int) hay double add(int) → gây mơ hồ, nên bị cấm.

- Ví dụ trong ngân hàng:
Giả sử bạn có nhiều cửa sổ giao dịch ngân hàng đều tên là “Giao dịch”:
  - Một cửa sổ nhận (CMND, số tiền) → rút tiền.
  - Một cửa sổ nhận (số thẻ, số tiền, OTP) → chuyển tiền.

-> Hệ thống phân biệt dựa vào loại giấy tờ bạn đưa ra (tham số), chứ không thể phân biệt bằng việc kết quả cuối cùng trả về là gì.
