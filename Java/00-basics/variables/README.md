# 📝 Variables trong Java

Biến (**Variable**) là vùng nhớ trong máy tính được đặt tên để lưu trữ dữ liệu.  
Trong Java, biến có **kiểu dữ liệu** (data type) xác định loại giá trị mà biến có thể chứa.  

---

## 🔑 Các loại biến trong Java

1. **Biến cục bộ (Local variable)**  
   - Khai báo trong method, constructor hoặc block.  
   - Chỉ tồn tại trong phạm vi được khai báo(khi kết thúc method/block thì biến bị xóa khỏi bộ nhớ).
   -   Không có giá trị mặc định → bắt buộc phải khởi tạo trước khi sử dụng.


2. **Biến instance (Instance variable)**  
   - Khai báo trong class nhưng **ngoài method,constructor hoặc block**.  
   - Gắn với đối tượng (object) → mỗi object có bản sao riêng của biến instance.  
   - Có giá trị mặc định.
   - Phạm vi truy cập: trong toàn bộ class (qua object).

3. **Biến static (Class variable)**  
   - Khai báo với từ khóa `static`.  
   - Gắn với **class**, không gắn với object cụ thể nên tất cả các object cùng chia sẻ 1 biến static.  
   - Có giá trị mặc định giống biến instance.
   - Truy cập thông qua ClassName.variableName hoặc object.variableName (khuyến khích dùng qua class).
   - Tồn tại suốt chương trình.

## 💳 Ví dụ: BankAccount
```java
public class BankAccount {
    // 🔵 Static variable (biến lớp)
    // Dùng chung cho tất cả tài khoản
    static String bankName = "TechBank";

    // 🟡 Instance variables (biến instance)
    // Mỗi tài khoản có số dư và số tài khoản riêng
    String accountNumber;
    double balance;

    // Constructor để khởi tạo tài khoản
    public BankAccount(String accountNumber, double initialBalance) {
        this.accountNumber = accountNumber;
        this.balance = initialBalance;
    }

    // Nạp tiền vào tài khoản
    public void deposit(double amount) {
        // 🟢 Local variable (biến cục bộ)
        // Chỉ dùng trong method deposit
        double newBalance = balance + amount;
        balance = newBalance;
        System.out.println("Nạp " + amount + " vào " + accountNumber);
    }

    // Rút tiền
    public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println("Rút " + amount + " từ " + accountNumber);
        } else {
            System.out.println("❌ Số dư không đủ!");
        }
    }

    // Hiển thị thông tin tài khoản
    public void displayInfo() {
        System.out.println("Ngân hàng: " + bankName);
        System.out.println("Số tài khoản: " + accountNumber);
        System.out.println("Số dư: " + balance);
        System.out.println("--------------------");
    }

    // Main để chạy thử
    public static void main(String[] args) {
        BankAccount acc1 = new BankAccount("001", 1000);
        BankAccount acc2 = new BankAccount("002", 2000);

        acc1.deposit(500); // dùng local variable newBalance
        acc2.withdraw(1000);

        acc1.displayInfo();
        acc2.displayInfo();

        // Thay đổi biến static
        BankAccount.bankName = "GlobalBank";

        acc1.displayInfo();
        acc2.displayInfo();
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
##  Quy tắc đặt tên biến trong Java
- Bắt đầu bằng chữ cái, $ hoặc _, không bắt đầu bằng số.
- Dùng camelCase: studentName, totalScore.
- Tên biến phải có ý nghĩa, dễ hiểu.
- Tránh trùng với từ khóa của Java (class, int, public, …).
