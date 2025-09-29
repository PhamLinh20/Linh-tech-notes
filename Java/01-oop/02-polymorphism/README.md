# 🎭 Tính đa hình (Polymorphism)
**Polymorphism (đa hình)** cho phép cùng một phương thức(method) hoặc đối tượng(object) có thể thực hiện các hành vi khác nhau tùy thuộc vào lớp thực tế mà nó thuộc về khi chương trình chạy (runtime).”

**Ví dụ:** 
Một sàn thương mại điện tử có nhiều loại dịch vụ giao hàng: Giao hàng thường, Giao hàng nhanh, Giao hàng quốc tế.
Tất cả các dịch vụ đều có hành vi chung là “tính phí giao hàng”, nhưng mỗi loại có cách tính khác nhau.

---
## ⚙️ Hoạt động của Polymorphism
Polymorphism hoạt động dựa trên cơ chế:
- **Compile-time Polymorphism (Static Polymorphism)** → Xác định phương thức **ngay lúc biên dịch**.  
- **Runtime Polymorphism (Dynamic Polymorphism)** → Xác định phương thức **khi chương trình đang chạy**.

---
## 📌 Các loại Polymorphism trong Java**
|  Loại Polymorphism | Thời điểm xác định | Cách thực hiện |
|----------------------|----------------------|------------------|
| **Method Overloading** | Compile-time (biên dịch) | Nhiều phương thức **cùng tên** nhưng **khác tham số** trong **cùng một lớp**. |
| **Method Overriding**  | Runtime (khi chạy)       | Lớp con **ghi đè** phương thức của lớp cha để **tùy biến hành vi**. |

---
### 1. Method Overloading
- Xảy ra khi **cùng một lớp** có nhiều phương thức **trùng tên** nhưng:
  - Khác **số lượng tham số**, hoặc
  - Khác **kiểu dữ liệu tham số**, hoặc khác **thứ tự kiểu dữ liệu tham số**.
- Không phụ thuộc vào **kiểu trả về**.

**Ví dụ:** 
```java
class Calculator {
    int add(int a, int b) {
        return a + b;
    }

    // Overloading: khác số lượng tham số
    int add(int a, int b, int c) {
        return a + b + c;
    }
}

public class Main {
    public static void main(String[] args) {
        Calculator calc = new Calculator();
        System.out.println(calc.add(2, 3));      // Kết quả: 5
        System.out.println(calc.add(1, 2, 3));   // Kết quả: 6
    }
}
```

---
### 2. Method Overriding
- **Định nghĩa:** Lớp con viết lại phương thức đã có trong lớp cha, nhưng vẫn giữ nguyên tên và danh sách tham số.
 Nhờ vậy, khi gọi phương thức từ đối tượng lớp con, phiên bản mới trong lớp con sẽ được chạy thay vì của lớp cha.
- `@Override`: Nếu định ghi đè nhưng lỡ viết sai tên phương thức hoặc tham số (nên thực tế không override mà vô tình tạo một phương thức mới), thì trình biên dịch sẽ báo lỗi giúp tránh nhầm lẫn.
- **Runtime Polymorphism:** Khi dùng một biến tham chiếu kiểu cha (superclass) nhưng trỏ tới một đối tượng kiểu con (subclass).
 Lúc chạy chương trình, Java sẽ quyết định gọi phương thức của lớp con hay lớp cha dựa trên đối tượng thực tế mà biến tham chiếu trỏ đến.

 **Ví dụ:** 
```java
 // Lớp cha: Dịch vụ giao hàng chung
class DeliveryService {
    public void calculateFee(double weight) {
        System.out.println("Tính phí giao hàng chung...");
    }
}

// Lớp con: Giao hàng thường
class StandardDelivery extends DeliveryService {
    @Override
    public void calculateFee(double weight) {
        double fee = 20000 + weight * 1000;
        System.out.println("Giao hàng thường: " + fee + " VND");
    }
}

// Lớp con: Giao hàng nhanh
class ExpressDelivery extends DeliveryService {
    @Override
    public void calculateFee(double weight) {
        double fee = 40000 + weight * 1500;
        System.out.println("Giao hàng nhanh: " + fee + " VND");
    }
}

// Lớp con: Giao hàng quốc tế
class InternationalDelivery extends DeliveryService {
    @Override
    public void calculateFee(double weight) {
        double fee = 100000 + weight * 5000;
        System.out.println("Giao hàng quốc tế: " + fee + " VND");
    }
}

// Chương trình chính
public class Main {
    public static void main(String[] args) {
        // Biến tham chiếu kiểu cha, đối tượng thực tế là lớp con (Runtime Polymorphism)
        DeliveryService service;

        service = new StandardDelivery();
        service.calculateFee(2.5);   // Gọi phương thức của StandardDelivery

        service = new ExpressDelivery();
        service.calculateFee(2.5);   // Gọi phương thức của ExpressDelivery

        service = new InternationalDelivery();
        service.calculateFee(2.5);   // Gọi phương thức của InternationalDelivery
    }
}

```

💡**Lưu ý :**
Trong Java, **“chữ ký” của phương thức** gồm:

- **Tên phương thức** (*method name*)  
- **Danh sách tham số** (*parameter list*: số lượng, kiểu dữ liệu, thứ tự)  

👉 **Không bao gồm**:  
- Kiểu trả về (*return type*)  
- Phạm vi truy cập (*access modifier*: `public`, `private`, …)  
---
