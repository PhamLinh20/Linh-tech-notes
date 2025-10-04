# 🌀 Tính trừu tượng (Abstraction)
**Abstraction(Trừu tượng)** dùng để ẩn đi phần chi tiết bên trong (cách một đối tượng hoạt động) và chỉ cho người dùng thấy chức năng cần thiết.
Nó tập trung vào **“cái gì làm”** thay vì **“làm như thế nào”**.

**Các đặc điểm chính của Abstraction**

- **Ẩn chi tiết phức tạp** → Người dùng chỉ quan tâm đến chức năng, không cần biết logic bên trong.
-  Abstract class có thể **chứa phương thức chưa có phần thân** (abstract method), và bắt buộc các lớp con phải triển khai.
-  **Dễ bảo trì & linh hoạt** → Khi thay đổi cách triển khai bên trong, phần code bên ngoài sử dụng abstraction sẽ không bị ảnh hưởng.

**Ví dụ:** Trong một ứng dụng bán hàng, có nhiều phương thức thanh toán khác nhau:

- Chuyển khoản ngân hàng 
- Thanh toán bằng thẻ tín dụng 
- Thanh toán qua ví điện tử 

Người dùng chỉ cần **thanh toán** mà không cần biết chi tiết các phương thức trên hoạt động như nào.

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

💡**Lưu ý:**  Static method (phương thức tĩnh) là phương thức thuộc về lớp (class) chứ không thuộc về đối tượng (object).
- Có thể gọi phương thức đó mà không cần tạo đối tượng của lớp.
- Nó được gắn với class chứ không gắn với từng instance.

**Ví dụ:** Thanh toán trong ứng dụng bán hàng
- Lớp cha `Payment`:
  - Đại diện cho khái niệm thanh toán chung, chứa thông tin như số tiền, loại tiền tệ.
  - Xác định hành vi chung là thanh toán, nhưng chưa mô tả chi tiết cách thực hiện.
- Các lớp con:
  - Chuyển khoản ngân hàng, Thẻ tín dụng, Ví điện tử.
  - Mỗi loại có đặc điểm riêng như: thông tin ngân hàng, số thẻ, nhà cung cấp ví.
  - Cách thực hiện thanh toán khác nhau tùy từng phương thức.

```java
// Abstract class: Payment
abstract class Payment {
    double amount;
    
 // Constructor
    Payment(double amount) {
        this.amount = amount;
    }

    // Phương thức trừu tượng: lớp con bắt buộc phải triển khai
    abstract void processPayment();

    // Phương thức bình thường: dùng chung cho tất cả các phương thức thanh toán
    void showAmount() {
        System.out.println("Số tiền thanh toán: " + amount + " VND");
    }
}

// Lớp con: Chuyển khoản ngân hàng
class BankTransfer extends Payment {
    BankTransfer(double amount) {
        super(amount);
    }

    @Override
    void processPayment() {
        System.out.println("Đang xử lý thanh toán qua **chuyển khoản ngân hàng**...");
        System.out.println("Thanh toán thành công qua ngân hàng!");
    }
}

// Lớp con: Thanh toán qua thẻ tín dụng
class CreditCardPayment extends Payment {
    CreditCardPayment(double amount) {
        super(amount);
    }

    @Override
    void processPayment() {
        System.out.println("Đang xử lý thanh toán qua **thẻ tín dụng**...");
        System.out.println("Thanh toán thành công qua thẻ tín dụng!");
    }
}

// Lớp con: Thanh toán qua ví điện tử
class EWalletPayment extends Payment {
    EWalletPayment(double amount) {
        super(amount);
    }

    @Override
    void processPayment() {
        System.out.println("Đang xử lý thanh toán qua **ví điện tử**...");
        System.out.println("Thanh toán thành công qua ví điện tử!");
    }
}

// Main: Người dùng chỉ cần thanh toán, không cần quan tâm phương thức nào
public class Main {
    public static void main(String[] args) {
        Payment payment1 = new BankTransfer(500000);
        Payment payment2 = new CreditCardPayment(1200000);
        Payment payment3 = new EWalletPayment(800000);

        payment1.showAmount();
        payment1.processPayment();

        System.out.println("---------------------");

        payment2.showAmount();
        payment2.processPayment();

        System.out.println("---------------------");

        payment3.showAmount();
        payment3.processPayment();
    }
}

```
**Kết quả:**
```java
Số tiền thanh toán: 500000.0 VND
Đang xử lý thanh toán qua **chuyển khoản ngân hàng**...
Thanh toán thành công qua ngân hàng!
---------------------
Số tiền thanh toán: 1200000.0 VND
Đang xử lý thanh toán qua **thẻ tín dụng**...
Thanh toán thành công qua thẻ tín dụng!
---------------------
Số tiền thanh toán: 800000.0 VND
Đang xử lý thanh toán qua **ví điện tử**...
Thanh toán thành công qua ví điện tử!
```

---
### 2. Interface
#### 2.1 Interface là gì?
Interface trong Java là một hợp đồng (contract) hoặc một tập hợp quy tắc mà một lớp hứa sẽ tuân theo.
- Nó định nghĩa một bộ phương thức trừu tượng (chỉ có chữ ký – signature, không có phần cài đặt).
- Bất kỳ lớp nào implements(thực hiện) interface thì bắt buộc phải cung cấp phần cài đặt cụ thể cho tất cả các phương thức mà interface yêu cầu.

**Ví dụ:**  Trong ngân hàng, PaymentMethod là quy định chung cho các cách thanh toán.
- Các hình thức như thẻ tín dụng, chuyển khoản, hay ví điện tử chỉ cần tuân theo quy định này thì đều có thể thực hiện giao dịch.

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
// Interface định nghĩa hành vi thanh toán
interface PaymentMethod {
    void pay();  // Phương thức abstract

    // Default method
    default void info() {
        System.out.println("This is a default method inside an interface");
    }

    // Static method
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
// Class triển khai (implements) Interface
class BankTransfer implements PaymentMethod {
    @Override
    public void pay() {
        System.out.println("Thanh toán qua chuyển khoản ngân hàng");
    }
}

``` 

```java
public class Main {
    public static void main(String[] args) {
        BankTransfer bankPayment = new BankTransfer();

        // Gọi phương thức abstract đã được triển khai
        bankPayment.pay();   
        // Output: Thanh toán qua chuyển khoản ngân hàng

        // Gọi default method từ Interface
        bankPayment.info();  
        // Output: This is a default method inside an interface

        // Gọi static method từ Interface
        PaymentMethod.displayRules();  
        // Output: Interface rules are being displayed
    }
}

```
---
#### 2.4 Đa kế thừa hành vi với Interface
Java không hỗ trợ đa kế thừa class, nhưng cho phép một class implements nhiều interface, rất hữu ích để gom nhiều hành vi khác nhau.

**Ví dụ:**
```java
// Interface định nghĩa hành vi thanh toán
interface Payable {
    void pay();
}

// Interface định nghĩa hành vi hoàn tiền
interface Refundable {
    void refund();
}

// Lớp EWallet vừa có thể thanh toán vừa có thể hoàn tiền
class EWallet implements Payable, Refundable {
    @Override
    public void pay() {
        System.out.println("Thanh toán qua ví điện tử");
    }

    @Override
    public void refund() {
        System.out.println("Hoàn tiền về ví điện tử");
    }
}

public class Main {
    public static void main(String[] args) {
        EWallet wallet = new EWallet();
        wallet.pay();     // Output: Thanh toán qua ví điện tử
        wallet.refund();  // Output: Hoàn tiền về ví điện tử
    }
}

```
-> `EWallet` vừa có thể thanh toán, vừa hoàn tiền mà không bị ràng buộc bởi giới hạn một class cha.

---
#### 2.5 Khi nào nên dùng Interface ?
#### a) **Định nghĩa giao diện chung cho nhiều lớp không liên quan trực tiếp**  
   - Khi có nhiều lớp **không cùng quan hệ kế thừa**, nhưng cần **chung một hành vi**.  
   - **Ví dụ:**  `BankTransfer` và `EWalletPayment` đều có khả năng thanh toán `(pay())`, nhưng rõ ràng chúng không nên cùng kế thừa từ một class cha
→ dùng interface Payable để gom hành vi thanh toán chung.

#### b) **Cần đa kế thừa hành vi**  
   - Trong Java, một class **chỉ extends được 1 class**,  nhưng **có thể implements nhiều interface**.  
   - Điều này rất hữu ích khi một đối tượng cần **nhiều vai trò khác nhau**.  
   - **Ví dụ:**  
     - `EWallet` vừa có thể thanh toán `(pay())` → implements `Payable`.
     - Vừa có thể hoàn tiền `(refund())` → implements `Refundable`.

#### c) **Tách biệt API và Implementation**  
   - Interface đóng vai trò như **API** (bản thiết kế công khai).  
   - Lớp cụ thể sẽ đóng vai trò **Implementation** (chi tiết triển khai).  
   - Giúp **dễ dàng bảo trì và mở rộng**:  Thay đổi bên trong lớp **không ảnh hưởng** đến phần code bên ngoài đang sử dụng interface.  
   - **Ví dụ:**  
     - `PaymentMethod` là interface định nghĩa phương thức `pay()`.
     - Các lớp như `BankTransfer`, `CreditCardPayment`, `EWalletPayment` sẽ cài đặt chi tiết cho từng hình thức thanh toán.
     - Khi muốn thêm phương thức thanh toán mới (ví dụ `QRPayment`), chỉ cần tạo class mới implements interface, không cần chỉnh sửa code cũ.

