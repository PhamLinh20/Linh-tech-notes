# 📝 Variables trong Java

Biến (**Variable**) là vùng nhớ trong máy tính được đặt tên để lưu trữ dữ liệu.  
Trong Java, biến có **kiểu dữ liệu** (data type) xác định loại giá trị mà biến có thể chứa.  

---

## 🔑 Các loại biến trong Java

1. **Biến cục bộ (Local variable)**  
   - Khai báo trong method, constructor hoặc block.  
   - Chỉ tồn tại trong phạm vi được khai báo(khi kết thúc method/block thì biến bị xóa khỏi bộ nhớ).
   -   Không có giá trị mặc định → bắt buộc phải khởi tạo trước khi sử dụng.

**Ví dụ:** Số tiền bạn rút từ ATM chỉ tồn tại trong lúc giao dịch, kết thúc giao dịch thì biến mất.
```java
public class ATM {
    public void withdraw() {
        int amount = 500; // Chỉ sử dụng trong phương thức này
        System.out.println("Withdraw amount: $" + amount);
    }
}
public class Main {
    public static void main(String[] args) {
        ATM atm = new ATM();
        atm.withdraw();
    }
}
```

2. **Biến instance (Instance variable)**  
   - Khai báo trong class nhưng **ngoài method,constructor hoặc block**.  
   - Gắn với đối tượng (object) → mỗi object có bản sao riêng của biến instance.  
   - Có giá trị mặc định.
   - Phạm vi truy cập: trong toàn bộ class (qua object).

**Ví dụ:** Mỗi tài khoản ngân hàng có chủ tài khoản và số dư riêng, không ai giống ai.
```java
public class BankAccount {
    // Gắn với từng đối tượng
    String accountHolder;
    double balance;

    public void showInfo() {
        System.out.println("Account Holder: " + accountHolder + ", Balance: $" + balance);
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc1 = new BankAccount();
        acc1.accountHolder = "Linh";
        acc1.balance = 5000;

        BankAccount acc2 = new BankAccount();
        acc2.accountHolder = "Ly";
        acc2.balance = 2000;

        acc1.showInfo(); // Account Holder: Linh, Balance: $5000
        acc2.showInfo(); // Account Holder: Ly, Balance: $2000
    }
}
``` 

3. **Biến static (Class variable)**  
   - Khai báo với từ khóa `static`.  
   - Gắn với **class**, không gắn với object cụ thể nên tất cả các object cùng chia sẻ 1 biến static.  
   - Có giá trị mặc định giống biến instance.
   - Truy cập thông qua ClassName.variableName hoặc object.variableName (khuyến khích dùng qua class).
   - Tồn tại suốt chương trình.

**Ví dụ:** Lãi suất ngân hàng là giá trị dùng chung cho tất cả các tài khoản.
```java
public class BankAccount {
    // Tất cả các object cùng chia sẻ 1 biến
    static double interestRate = 3.5; // 3.5%

    String accountHolder;
    double balance;

    public void showInterestRate() {
        System.out.println("Current Interest Rate: " + interestRate + "%");
    }
}

public class Main {
    public static void main(String[] args) {
        BankAccount acc1 = new BankAccount();
        BankAccount acc2 = new BankAccount();

        acc1.showInterestRate(); // Lãi suất hiện tại: 3.5%
        acc2.showInterestRate(); // Lãi suất hiện tại: 3.5%

        // Cập nhật biến static(lãi suất)-> ảnh hưởng đến tất cả objects(accounts)
        BankAccount.interestRate = 4.0;

        acc1.showInterestRate(); // Lãi suất hiện tại: 4.0%
        acc2.showInterestRate(); // Lãi suất hiện tại: 4.0%
    }
}
```
---
## 🔎 Kiểu dữ liệu cơ bản (Primitive types)

| Kiểu dữ liệu | Kích thước | Giá trị mặc định | Ví dụ |
|--------------|------------|------------------|-------|
| `byte`       | 8-bit      | 0                | `byte a = 100;` |
| `short`      | 16-bit     | 0                | `short b = 20000;` |
| `int`        | 32-bit     | 0                | `int c = 10;` |
| `long`       | 64-bit     | 0L               | `long d = 100000L;` |
| `float`      | 32-bit     | 0.0f             | `float e = 3.14f;` |
| `double`     | 64-bit     | 0.0              | `double f = 3.14159;` |
| `char`       | 16-bit     | '\u0000'         | `char g = 'A';` |
| `boolean`    | 1-bit      | false            | `boolean h = true;` |

Ngoài ra, còn có **kiểu tham chiếu (Reference types)**: `String`, `Array`, `Object`, ...

---

## ⚡ Cú pháp khai báo biến

```java
<kiểu_dữ_liệu> <tên_biến> = <giá_trị_khởi_tạo>;
int age = 20;
double pi = 3.14159;
char grade = 'A';
boolean isActive = true; 
```
---
## 💡 Quy tắc đặt tên biến trong Java
- Bắt đầu bằng chữ cái, $ hoặc _, không bắt đầu bằng số.
- Dùng camelCase: studentName, totalScore.
- Tên biến phải có ý nghĩa, dễ hiểu.
- Tránh trùng với từ khóa của Java (class, int, public, …).
