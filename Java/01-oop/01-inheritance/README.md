# 🧬 Tính kế thừa (Inheritance)
Kế thừa là một tính năng cốt lõi của lập trình hướng đối tượng (OOP). Nó cho phép một lớp (class) kế thừa (tức sử dụng lại) các thuộc tính (fields/biến) và phương thức (methods) từ một lớp(class) khác.

Trong Java, kế thừa là tạo ra 1 lớp(class) mới dựa trên lớp(class) đã có, lớp mới có thể sử dụng lại các thuộc tính và phương thức của lớp đó.

**Ví dụ:**
Các lớp `car` , `truck` có thể tạo ra dựa trên lớp `vehicle` và kế thừa các thuộc tính(tốc độ,bánh xe) hay các phương thức(tăng tốc, giảm tốc) của lớp `vehicle` .

---
## 📝 Cú pháp (Syntax)
```java
class lớp con(ChildClass) extends lớp cha (ParentClass) {  

    // Thêm thuộc tính và phương thức 
}
```
💡**Lưu ý:** 
Trong Java, kế thừa được triển khai bằng cách sử dụng từ khóa `extends` (mở rộng). Lớp kế thừa được gọi là lớp con (subclass/child class) và lớp được kế thừa được gọi là lớp cha (superclass/parent class).

---

## 🗝 Thuật ngữ chính 
| Thuật ngữ                | Ý nghĩa |
|-----------------------------|------------|
| **Superclass / Parent class** | Lớp cha, chứa các **thuộc tính (fields)** và **phương thức (methods)** chung mà các lớp con có thể kế thừa. |
| **Subclass / Child class**   | Lớp con, kế thừa từ lớp cha và có thể **mở rộng thêm** thuộc tính hoặc phương thức riêng. |
| **extends**                  | Từ khóa dùng để tạo quan hệ kế thừa giữa lớp con và lớp cha. |
| **`super` keyword**          | Dùng để **gọi constructor**, **fields**, hoặc **methods** từ lớp cha. |

---
## ⚙️ Cách hoạt động 
### 1. Khai báo quan hệ kế thừa
- Lớp con dùng từ khóa `extends` để kế thừa từ lớp cha.
- Java chỉ cho phép một lớp con kế thừa duy nhất một lớp cha (single inheritance).
- Khi đã kế thừa, lớp con tự động nhận tất cả các thuộc tính và phương thức (trừ private) từ lớp cha.

**Ví dụ:**
```java
// Lớp cha
class Vehicle {
    int wheels;  // Số bánh xe
    int speed;   // tốc độ hiện tại

    // Phương thức để tăng tốc
    void accelerate() {
        speed += 10;
        System.out.println("Accelerating! New speed: " + speed + " km/h");
    }
}

// lớp con Car kế thừa từ lớp cha Vehicle
class Car extends Vehicle {
    // có thể thêm thuộc tính 
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car();
        myCar.wheels = 4;
        myCar.speed = 50;

        System.out.println("Number of wheels: " + myCar.wheels);
        System.out.println("Initial speed: " + myCar.speed + " km/h");

        // Gọi phương thức tăng tốc được kế thừa từ Vehicle
        myCar.accelerate();  // Tăng tốc độ thêm 10
    }
}
```

**Kết quả:**
```java
Number of wheels: 4
Initial speed: 50 km/h
Accelerating! New speed: 60 km/h
``` 
---
### 2. Sử dụng từ khóa `super`
- `super` gọi constructor của lớp cha (phải đặt ở dòng đầu tiên trong constructor lớp con).
- Dùng `super.methodName()` hoặc `super.field` truy cập đến phương thức hoặc biến của lớp cha khi bị lớp con ghi đè.

**Ví dụ:**
```java
// Lớp cha: Vehicle
class Vehicle {
    int wheels;

    // Constructor của Vehicle
    Vehicle(int wheels) {
        this.wheels = wheels;
    }

    void showWheels() {
        System.out.println("Number of wheels: " + wheels);
    }
}

// Lớp con: Car kế thừa từ Vehicle
class Car extends Vehicle {
    String brand;

    // Constructor của Car gọi constructor của Vehicle bằng super
    Car(String brand, int wheels) {
        super(wheels); // Gọi constructor của Vehicle
        this.brand = brand;
    }

    void showInfo() {
        System.out.println("Brand: " + brand);
        showWheels(); // Gọi phương thức của lớp cha (hoặc dùng super.showWheels())
    }
}

public class Main {
    public static void main(String[] args) {
        Car myCar = new Car("Toyota", 4);
        myCar.showInfo();
    }
}
```

💡**Lưu ý:**  `@Override`

- `@Override` được dùng khi bạn định nghĩa lại (ghi đè) một phương thức đã có trong lớp cha.
- Phương thức ghi đè phải có cùng tên, kiểu trả về, và tham số với phương thức trong lớp cha.
- `@Override` giúp:
    - **Phát hiện lỗi** nếu bạn viết sai tên hoặc sai tham số so với lớp cha.
    - Làm rõ ý định rằng bạn đang ghi đè phương thức.

- Khi ghi đè, bạn có thể sử dụng `super.methodName()` để gọi phương thức gốc của lớp cha bên trong phương thức mới.

---