# 🧬 Tính kế thừa (Inheritance)
**Inheritance(kế thừa)** cho phép một lớp (class) kế thừa (tức sử dụng lại) các thuộc tính (fields/biến) và phương thức (methods) từ một lớp(class) khác.

Trong Java, kế thừa là tạo ra 1 lớp(class) mới dựa trên lớp(class) đã có, lớp mới có thể sử dụng lại các thuộc tính và phương thức của lớp đó.

**Ví dụ:**
Một ngân hàng có nhiều loại tài khoản : tài khoản tiết kiệm, tài khoản tín dụng,...
Tất cả các loại tài khoản này chia sẻ chung các thuộc tính (số tài khoản, tên chủ tài khoản, số dư hiện tại,...) và hành vi cơ bản(nạp tiền, rút tiền, kiểm tra số dư,...).

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
// Lớp cha: Tài khoản ngân hàng chung
class BankAccount {
    String ownerName;  // Tên chủ tài khoản
    double balance;    // Số dư

    // Phương thức gửi tiền
    void deposit(double amount) {
        balance += amount;
        System.out.println("Đã nạp " + amount + " VND. Số dư mới: " + balance + " VND");
    }

    // Phương thức rút tiền
    void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
            System.out.println("Đã rút " + amount + " VND. Số dư còn lại: " + balance + " VND");
        } else {
            System.out.println("Số dư không đủ để rút!");
        }
    }
}

// Lớp con: Tài khoản tiết kiệm
class SavingsAccount extends BankAccount {
    double interestRate = 0.05; // 5% lãi suất

    // Phương thức tính lãi (riêng cho tài khoản tiết kiệm)
    void addInterest() {
        double interest = balance * interestRate;
        balance += interest;
        System.out.println(" Tiền lãi cộng thêm: " + interest + " VND. Số dư hiện tại: " + balance + " VND");
    }
}

// Chương trình chính
public class Main {
    public static void main(String[] args) {
        // Tạo tài khoản tiết kiệm
        SavingsAccount account = new SavingsAccount();
        account.ownerName = "Nguyễn Văn A";
        account.balance = 5_000_000;

        System.out.println("Chủ tài khoản: " + account.ownerName);
        System.out.println("Số dư ban đầu: " + account.balance + " VND");

        // Gọi phương thức kế thừa từ BankAccount
        account.deposit(2_000_000);     // Gửi thêm tiền
        account.withdraw(1_000_000);    // Rút tiền

        // Gọi phương thức riêng của SavingsAccount
        account.addInterest();          // Tính lãi suất
    }
}

```

**Kết quả:**
```java
Chủ tài khoản: Nguyễn Văn A
Số dư ban đầu: 5000000.0 VND
Đã nạp 2000000.0 VND. Số dư mới: 7000000.0 VND
Đã rút 1000000.0 VND. Số dư còn lại: 6000000.0 VND
Tiền lãi cộng thêm: 300000.0 VND. Số dư hiện tại: 6300000.0 VND

``` 
---
### 2. Sử dụng từ khóa `super`
- `super` gọi constructor của lớp cha (phải đặt ở dòng đầu tiên trong constructor lớp con).
- Dùng `super.methodName()` hoặc `super.field` truy cập đến phương thức hoặc biến của lớp cha khi bị lớp con ghi đè.

**Ví dụ:**
```java
// Lớp cha: Tài khoản ngân hàng chung
class BankAccount {
    String ownerName;
    double balance;

    // Constructor của BankAccount
    BankAccount(String ownerName, double balance) {
        this.ownerName = ownerName;
        this.balance = balance;
    }

    void displayInfo() {
        System.out.println("Chủ tài khoản: " + ownerName);
        System.out.println("Số dư: " + balance + " VND");
    }
}

// Lớp con: Tài khoản tiết kiệm kế thừa từ BankAccount
class SavingsAccount extends BankAccount {
    double interestRate;

    // Constructor lớp con gọi constructor lớp cha bằng super
    SavingsAccount(String ownerName, double balance, double interestRate) {
        super(ownerName, balance); // Gọi constructor của BankAccount
        this.interestRate = interestRate;
    }

    // Ghi đè phương thức displayInfo để hiển thị thêm lãi suất
    @Override
    void displayInfo() {
        super.displayInfo(); // Gọi phương thức lớp cha để tái sử dụng
        System.out.println("Lãi suất: " + (interestRate * 100) + "%");
    }
}

public class Main {
    public static void main(String[] args) {
        SavingsAccount savings = new SavingsAccount("Nguyễn Văn A", 5000000, 0.05);
        savings.displayInfo();
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

**Ví dụ:**
Giả sử ngân hàng có một lớp cha `BankAccount` đại diện cho tài khoản chung:
- Chứa phương thức `calculateInterest()` dùng để tính lãi.
- Phương thức này sẽ được ghi đè (override) ở lớp con để tính toán riêng cho từng loại tài khoản.
```java
// Lớp cha: BankAccount
class BankAccount {
    String ownerName;
    double balance;

    public BankAccount(String ownerName, double balance) {
        this.ownerName = ownerName;
        this.balance = balance;
    }

    // Phương thức tính lãi suất chung
    public void calculateInterest() {
        System.out.println("Tài khoản chung không có lãi suất đặc biệt.");
    }
}

// Lớp con: SavingsAccount kế thừa BankAccount
class SavingsAccount extends BankAccount {
    double interestRate;

    public SavingsAccount(String ownerName, double balance, double interestRate) {
        super(ownerName, balance);
        this.interestRate = interestRate;
    }

    // Ghi đè phương thức calculateInterest
    @Override
    public void calculateInterest() {
        double interest = balance * interestRate;
        System.out.println("Tài khoản tiết kiệm của " + ownerName +
                           " nhận lãi: " + interest + " VND");
    }
}

// Chương trình chính
public class Main {
    public static void main(String[] args) {
        BankAccount acc1 = new BankAccount("Nguyễn Văn A", 5_000_000);
        BankAccount acc2 = new SavingsAccount("Trần Thị B", 10_000_000, 0.05);

        acc1.calculateInterest(); // Gọi phương thức gốc của BankAccount
        acc2.calculateInterest(); // Gọi phương thức đã được override trong SavingsAccount
    }
}

```
- Ngân hàng có thể thêm các loại tài khoản khác như `CheckingAccount`, `CreditAccount`...
- Mỗi loại tài khoản chỉ cần ghi đè phương thức calculateInterest() với cách tính riêng.
- Giúp mở rộng hệ thống dễ dàng mà không cần thay đổi code gốc.

---