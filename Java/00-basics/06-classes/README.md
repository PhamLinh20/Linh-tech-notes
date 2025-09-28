# 🏗️ Classes 
Trong Java, **class (lớp)** là **bản thiết kế (blueprint)** dùng để tạo ra **đối tượng (object)**.  
- **Class** định nghĩa các **thuộc tính (fields)** và **hành vi (methods)** mà các đối tượng sẽ có.  
- **Object** là **thực thể cụ thể** được tạo ra từ class, có **giá trị dữ liệu riêng**.

**Ví dụ:** Hãy hình dung class giống như một bản thiết kế cho tài khoản ngân hàng.

Trong bản thiết kế này, mỗi tài khoản sẽ có:
  - Thuộc tính: tên chủ tài khoản, số dư.
  - Hành vi: nạp tiền, rút tiền, xem thông tin.

Khi một khách hàng mở tài khoản, hệ thống sẽ tạo ra một đối tượng (object) dựa trên bản thiết kế đó.
Mỗi tài khoản được tạo ra hoạt động riêng biệt, nhưng tất cả đều tuân theo cùng một khuôn mẫu do class định nghĩa.

---
## 🧩 Thành phần của class
### 1. Thuộc tính (Fields / Variables)
- Lưu trữ **trạng thái** hoặc **thông tin** của đối tượng.  
- **Ví dụ:** `tên`, `số dư`, `tuổi`...
### 2. Phương thức (Methods)
- Xác định **hành vi** của đối tượng.  
 **Ví dụ:** `nạp tiền`, `rút tiền`, `xem số dư`,...
 ### 3. Constructor (Hàm khởi tạo)
 - **Constructor** là một **hàm đặc biệt** trong class, **tự động chạy** khi tạo object.  
- Tên của constructor **phải trùng với tên class** và **không có kiểu trả về**.  
- Dùng để:
  - **Gán giá trị ban đầu** cho các thuộc tính.
  - Thiết lập trạng thái mặc định cho object.

 **Ví dụ:**
Khi mở tài khoản ngân hàng, hệ thống sẽ **tự động khởi tạo** một hồ sơ khách hàng với thông tin cơ bản như tên, số tài khoản, số dư ban đầu.

---
## ⚡ Các thao tác cơ bản
### 1. Định nghĩa một class
- Định nghĩa một lớp với tên, thuộc tính (biến), và phương thức (hàm).

**Ví dụ:**
```java
public class BankAccount {
    // Thuộc tính
    String ownerName;
    double balance;

    // Constructor
    public BankAccount(String name, double initialBalance) {
        ownerName = name;
        balance = initialBalance;
    }

    // Phương thức
    public void deposit(double amount) {
        balance += amount;
    }

    public void withdraw(double amount) {
        if (balance >= amount) {
            balance -= amount;
        } else {
            System.out.println("Số dư không đủ!");
        }
    }

    public void displayInfo() {
        System.out.println(ownerName + " - Số dư: " + balance);
    }
}
```

---
### 2. Tạo object từ class
- Dùng từ khóa `new` để tạo ra một thực thể cụ thể.

**Ví dụ:**
```java
public class Main {
    public static void main(String[] args) {
        // Tạo một object từ class BankAccount
        BankAccount acc1 = new BankAccount("Nguyễn Văn A", 5000000);

        // Gọi phương thức
        acc1.deposit(2000000);        // Nạp tiền
        acc1.withdraw(3000000);       // Rút tiền
        acc1.displayInfo();           // Hiển thị thông tin
    }
}
```
---
## ⚠️ Các lưu ý quan trọng khi làm việc với Class
### 1. Tên class  
   - Bắt buộc **viết hoa chữ cái đầu** (theo quy tắc PascalCase).  
   - Ví dụ: `BankAccount`, `CustomerInfo`, `Student`.
### 2. Tên file phải trùng với tên class  
   - Nếu class là `BankAccount`, thì file phải lưu là **`BankAccount.java`**.
   - Nếu không, trình biên dịch sẽ báo lỗi.
### 3. Mỗi file chỉ nên có 1 class `public`
   - Có thể chứa nhiều class trong một file, nhưng chỉ **1 class được khai báo public**. 
   - Nếu có nhiều class `public` thì Java sẽ không biết “class chính” của file là gì → lỗi biên dịch. 
   - Class public phải trùng tên file.
### 4. Constructor đặc biệt
   - Nếu **không tự định nghĩa constructor**, Java sẽ tự tạo **constructor mặc định** (không tham số).  
   - Nếu đã tự tạo một constructor, **constructor mặc định sẽ không còn tồn tại** trừ khi bạn tự định nghĩa thêm.
### 5. Class là kiểu dữ liệu tham chiếu (reference type)  
   - Khi gán object này cho biến khác, **cả hai biến cùng trỏ đến một vùng nhớ**.
- **Ví dụ:**
 ```java
BankAccount acc1 = new BankAccount("A", 1000);
BankAccount acc2 = acc1;
acc2.deposit(500);
System.out.println(acc1.balance); // 1500, vì acc1 và acc2 cùng tham chiếu
```
### 6. Một class có thể tạo nhiều object 
- Các object được tạo từ cùng một class nhưng có **dữ liệu riêng biệt**.
- Ví dụ: Mỗi khách hàng có **tên**, **số dư**, **số tài khoản** riêng.

