# 🛡️ Tính đóng gói (Encapsulation)

## 📖 Khái niệm
**Encapsulation (Tính đóng gói)** là một trong **4 tính chất cơ bản** của lập trình hướng đối tượng (OOP). Dùng để gói gọn dữ liệu(biến) và hành vi(phương thức) vào trong một class, chỉ cho phép bên ngoài truy cập thông qua các **phương thức được cung cấp** (public methods). 

**Mục đích:**
- Bảo vệ dữ liệu: Không cho phép truy cập và thay đổi trực tiếp từ bên ngoài.
- Quản lý và kiểm soát dữ liệu: Đảm bảo dữ liệu luôn hợp lệ, tránh lỗi.
- Giảm sự phụ thuộc: Giúp hệ thống dễ bảo trì, nâng cấp, và mở rộng.
- Che giấu sự phức tạp: Người dùng chỉ cần biết phương thức `public`, không quan tâm đến chi tiết bên trong.
---
## 🔑 Các phạm vi truy cập (Access Modifiers)

| Từ khóa        | Mức độ truy cập                                                                                 |
|-------------------|----------------------------------------------------------------------------------------------------|
| **`public`**      | Truy cập từ **mọi nơi**, kể cả ngoài package.                                                     |
| **`protected`**   | Truy cập trong **cùng package** hoặc từ **lớp con (subclass)**.                                   |
| **`default`** *(không ghi gì)* | Chỉ truy cập **trong cùng package**.                                                |
| **`private`**     | Chỉ truy cập được **trong chính lớp đó**, bên ngoài **không thể truy cập trực tiếp**.            |

💡**Lưu ý:** Nếu không khai báo bất kỳ modifier nào sẽ được xem như dùng default.

---
## 🔒 Cách thực hiện Encapsulation
### 1. Khai báo các biến trong class là private
- Các biến chỉ có thể được truy cập trực tiếp từ **bên trong chính lớp đó**.
- Bên ngoài **không thể thay đổi giá trị trực tiếp**.
### 2. Cung cấp Getter và Setter (phương thức công khai `public`)
- **Getter** → Dùng để **lấy dữ liệu** từ biến `private`.
- **Setter** → Dùng để **cập nhật dữ liệu**.

**Ví dụ** 
```java
public class Person {
  private String name; 

  // Getter
  public String getName() {
    return name;
  }

  // Setter
  public void setName(String name) {
    this.name = name;
  }
}
public class Main {
  public static void main(String[] args) {
    Person per1 = new Person();
    per1.setName("Linh"); // Gán giá trị của biến name là "Linh"
    System.out.println(per1.getName());
  }
}
```
---
## ❌ Các lỗi thường gặp
### 1. Sử dụng sai phạm vi truy cập
Lỗi: Chọn Access Modifier sai, ví dụ dùng `protected` hoặc `public` cho dữ liệu nhạy cảm, cho phép truy cập từ bên ngoài mà không cần kiểm soát.

**Ví dụ sai**
```java
public class Person {
    protected String name; // protected cho phép class con hoặc package khác truy cập
}
```
-> Đặt biến là `private` để giới hạn quyền truy cập, chỉ public những gì thật sự cần thiết (Getter/Setter).

--- 
### 2. Không kiểm tra dữ liệu đầu vào trong `Setter`
Lỗi:
 `Setter` gán dữ liệu mà không kiểm tra giá trị, dẫn đến dữ liệu sai hoặc lỗi logic trong hệ thống.
 
**Ví dụ sai**
```java
public class Product {
    private double price;

    // Không kiểm tra dữ liệu đầu vào
    public void setPrice(double price) {
        this.price = price;
    }

    public double getPrice() {
        return price;
    }
}

public class Main {
    public static void main(String[] args) {
        Product p = new Product();
        p.setPrice(-100); // Giá âm không hợp lệ
        System.out.println("Giá sản phẩm: " + p.getPrice());
    }
}
```
- Dữ liệu sai (-100) làm hệ thống tính toán sai, gây ra lỗi nghiêm trọng.

