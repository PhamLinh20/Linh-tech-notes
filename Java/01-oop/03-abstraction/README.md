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
## 📌 Các cách triển khai Abstraction
Java cung cấp 2 cách để thực hiện Abstraction(trừu tượng) : 
- Abstract Classes : Trừu tượng 1 phần (Partial Abstraction)
- Interface : 100% trừu tượng (100% Abstraction)

---

### 1. Abstract Class
- Được khai báo bằng từ khóa **`abstract`**.  
- Có thể chứa cả:  
  - **Phương thức trừu tượng** (chỉ khai báo, không có thân hàm).  
  - **Phương thức bình thường** (có code sẵn).  
- Có thể chứa **thuộc tính (fields), constructor và cả static methods**.  
- **Không thể tạo đối tượng trực tiếp** từ abstract class.  
- Được dùng để **kế thừa** – các lớp con phải **triển khai (override)** các phương thức trừu tượng.  
- Thích hợp khi các lớp có **mối quan hệ gần gũi**, chia sẻ một số logic chung, nhưng vẫn **khác nhau ở một vài hành vi**.  
- Hỗ trợ **tái sử dụng code** thông qua việc chia sẻ phương thức/thuộc tính chung cho nhiều lớp con.  

**Ví dụ:** Shape (Hình học)
- **Lớp cha `Shape`:**  
  - Có các **thuộc tính chung** như `color`, `size`.  
  - Có các **hành vi chung**:  
    - `draw()` (có thể có sẵn code).  
    - `calculateArea()` (chưa có code, để lớp con tự triển khai).  

- **Các lớp con (`Circle`, `Square`, `Triangle`) kế thừa từ `Shape`:**  
  - Mỗi hình có thể thêm **đặc điểm riêng**(`radius` của `Circle`, `sideLength` của `Square` )
  - Có **hành vi khác nhau** (cách tính diện tích khác nhau cho từng hình)

```java
// Abstract class Shape
abstract class Shape {
    String color;

    // Constructor
    Shape(String color) {
        this.color = color;
    }

    // Phương thức trừu tượng (không có body)
    abstract double calculateArea();

    // Phương thức bình thường (có body)
    void displayColor() {
        System.out.println("Color: " + color);
    }
}

// Lớp con Circle
class Circle extends Shape {
    double radius;

    Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    double calculateArea() {
        return Math.PI * radius * radius;
    }
}

// Lớp con Square
class Square extends Shape {
    double side;

    Square(String color, double side) {
        super(color);
        this.side = side;
    }

    @Override
    double calculateArea() {
        return side * side;
    }
}

// Main
public class Main {
    public static void main(String[] args) {
        Shape s1 = new Circle("Red", 5);
        Shape s2 = new Square("Blue", 4);

        s1.displayColor(); // Color: Red
        System.out.println("Area: " + s1.calculateArea());

        s2.displayColor(); // Color: Blue
        System.out.println("Area: " + s2.calculateArea());
    }
}
```

---
### 2. Interface
#### 2.1 Interface là gì?
Interface trong Java là một hợp đồng (contract) hoặc một tập hợp quy tắc mà một lớp hứa sẽ tuân theo.
- Nó định nghĩa một bộ phương thức trừu tượng (chỉ có chữ ký – signature, không có phần cài đặt).
- Bất kỳ lớp nào implements(thực hiện) interface thì bắt buộc phải cung cấp phần cài đặt cụ thể cho tất cả các phương thức mà interface yêu cầu.

**Ví dụ:**  Ổ cắm điện và các thiết bị điện.

- Interface: `ElectricSocket` quy định các cổng và điện áp.
- Thiết bị như `Fan`, `Laptop` chỉ cần tuân thủ đúng interface để có thể kết nối và sử dụng.

---
#### 2.2 Đặc điểm chính
|  Đặc điểm | Giải thích |
|------------|--------------|
| **Phương thức** | Mặc định là **`public abstract`** (chỉ định nghĩa, không có phần thân). |
| **Biến (Fields)** | Mặc định là **`public static final`** → hằng số, phải gán giá trị ngay khi khai báo. |
| **Đa kế thừa hành vi** | Một class có thể `implements` **nhiều interface** cùng lúc → giải quyết vấn đề đa kế thừa. |
| **Access modifier** | Không thể khai báo `private` hoặc `protected` cho phương thức trong interface. |
| **Từ Java 8+** | Interface có thể chứa: <br> - `default methods` (có sẵn phần thân). <br> - `static methods`. |
| **Không có constructor** | Interface **không thể khởi tạo trực tiếp** và **không có constructor**. |

---
#### 2.3 Cú pháp cơ bản
**Khai báo Interface:**
- Dùng từ khóa interface để khai báo.
- Cú pháp:
```java
access_modifier interface InterfaceName {
    // khai báo hằng số
    // khai báo phương thức trừu tượng (chỉ có signature, không có body)
    // (từ Java 8) có thể có default method và static method
}
```

- **Ví dụ:**
```java
interface InterfaceName {
    // Hằng số
    int MAX_SPEED = 120; // public static final

    // Phương thức trừu tượng (mặc định là public abstract)
    void start();
    void stop();

    // Default method (Java 8+)
    default void info() {
        System.out.println("This is a default method inside an interface");
    }

    // Static method (Java 8+)
    static void displayRules() {
        System.out.println("Interface rules are being displayed");
    }
}
```
**Triển khai Interface:**
- Một class dùng từ khóa `implements` để cài đặt (triển khai) interface.
- Khi implements, class phải viết code cho tất cả các phương thức abstract.

**Ví dụ:**
```java
class Car implements InterfaceName {
    @Override
    public void start() {
        System.out.println("Car started ");
    }

    @Override
    public void stop() {
        System.out.println("Car stopped ");
    }
}
``` 

```java
// Main
public class Main {
    public static void main(String[] args) {
        Car car = new Car();
        car.start();  // Output: Car started 
        car.stop();   // Output: Car stopped 
        
        // Gọi default method
        car.info();   // Output: This is a default method inside an interface
        
        // Gọi static method từ Interface
        InterfaceName.displayRules(); // Output: Interface rules are being displayed
    }
}
```
---
#### 2.4 Đa kế thừa hành vi với Interface
Java không hỗ trợ đa kế thừa class, nhưng cho phép một class implements nhiều interface, rất hữu ích để gom nhiều hành vi khác nhau.

**Ví dụ:**
```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

// Lớp Duck kế thừa cả 2 hành vi: bay và bơi
class Duck implements Flyable, Swimmable {
    @Override
    public void fly() {
        System.out.println("Duck is flying");
    }

    @Override
    public void swim() {
        System.out.println("Duck is swimming");
    }
}

public class Main {
    public static void main(String[] args) {
        Duck duck = new Duck();
        duck.fly();   // Output: Duck is flying 
        duck.swim();  // Output: Duck is swimming 
    }
}
```
---
#### 2.5 Khi nào nên dùng Interface ?
#### a) **Định nghĩa giao diện chung cho nhiều lớp không liên quan trực tiếp**  
   - Khi có nhiều lớp **không cùng quan hệ kế thừa**, nhưng cần **chung một hành vi**.  
   - **Ví dụ:**  `Bird` và `Airplane` đều có khả năng `fly()`,  nhưng rõ ràng chúng **không nên cùng kế thừa từ một lớp cha** → dùng `interface Flyable`.

#### b) **Cần đa kế thừa hành vi**  
   - Trong Java, một class **chỉ extends được 1 class**,  nhưng **có thể implements nhiều interface**.  
   - Điều này rất hữu ích khi một đối tượng cần **nhiều vai trò khác nhau**.  
   - **Ví dụ:**  
     - `Duck` vừa là `Flyable` (có thể bay)  vừa là `Swimmable` (có thể bơi).  
     - `class Duck implements Flyable, Swimmable`.

#### c) **Tách biệt API và Implementation**  
   - Interface đóng vai trò như **API** (bản thiết kế công khai).  
   - Lớp cụ thể sẽ đóng vai trò **Implementation** (chi tiết triển khai).  
   - Giúp **dễ dàng bảo trì và mở rộng**:  Thay đổi bên trong lớp **không ảnh hưởng** đến phần code bên ngoài đang sử dụng interface.  
   - **Ví dụ:**  
     - `NotificationService` là interface định nghĩa phương thức `sendNotification()`.  
     - Các lớp triển khai như `EmailNotification`, `SMSNotification`, `PushNotification`  
       cài đặt chi tiết gửi thông báo qua từng kênh.  
     - Khi muốn thêm kênh mới (ví dụ `SlackNotification`),  chỉ cần **tạo class mới implement interface**, không cần thay đổi logic cũ.

