# 🧵 Chuỗi (String)
Trong lập trình **Java**, **String (chuỗi)** là một **đối tượng đặc biệt** dùng để **lưu trữ và thao tác với văn bản**.  
Một **String** về bản chất là **một chuỗi các ký tự (sequence of characters)** được đặt trong **dấu ngoặc kép (`" "`)**, ví dụ: `"Hello"`.

- Mỗi ký tự trong chuỗi được lưu trữ với **16-bit**, tuân theo chuẩn **UTF-16 encoding**.
- Chuỗi trong Java là **immutable (bất biến)** → khi thay đổi giá trị, **Java sẽ tạo ra một đối tượng String mới** thay vì chỉnh sửa trực tiếp chuỗi ban đầu.
- Một chuỗi **hoạt động tương tự mảng ký tự**, cho phép truy cập từng ký tự qua **chỉ số (index)**.  
- Java cung cấp **API mạnh mẽ và linh hoạt** để xử lý chuỗi, hỗ trợ nhiều thao tác.

💡**Lưu ý:** API trong String là tập hợp các phương thức (methods) mà Java cung cấp sẵn để làm việc với chuỗi

---
## ⚡ Các thao tác cơ bản
### 1. Khởi tạo chuỗi
Trong Java, có **2 cách phổ biến** để khởi tạo một đối tượng `String`.  
Mặc dù cùng lưu trữ văn bản, nhưng **cách thức hoạt động và vùng nhớ quản lý** là khác nhau.
#### 1.1 Khởi tạo bằng Literal (chuỗi trực tiếp)
Cách này thường dùng nhất và **tiết kiệm bộ nhớ**.  
Khi bạn gán một chuỗi trực tiếp bằng dấu ngoặc kép (`" "`), Java sẽ kiểm tra **String Pool** (bộ nhớ đặc biệt trong Java):
- Nếu chuỗi **chưa tồn tại**, Java sẽ **tạo mới** và lưu vào String Pool.
- Nếu chuỗi **đã tồn tại**, Java sẽ **tái sử dụng đối tượng cũ**, không tạo mới → tiết kiệm bộ nhớ.

**Cú pháp:**
```java
String s1 = "Hello";
String s2 = "Hello"; // s2 tái sử dụng cùng đối tượng với s1
```
**Minh họa bộ nhớ:**
```java
String Pool:
    ┌─────────────┐
    │   "Hello"   │  ← s1, s2 cùng trỏ đến đây
    └─────────────┘
```
💡**Lưu ý:** Luôn ưu tiên dùng literal khi không có yêu cầu đặc biệt, vì nó tiết kiệm bộ nhớ và hiệu suất tốt hơn.
#### 1.2 Khởi tạo bằng từ khóa `new`
Cách này luôn tạo ra một đối tượng mới trong bộ nhớ Heap, ngay cả khi trong String Pool đã tồn tại chuỗi có cùng nội dung.

Điều này đảm bảo bạn có một đối tượng độc lập, tách biệt hoàn toàn với các chuỗi khác.

**Cú pháp:**
```java
String s3 = new String("Hello");
```
**Minh họa bộ nhớ:**
```java
Heap:
    ┌─────────────┐
    │   "Hello"   │  ← s3 là đối tượng hoàn toàn mới
    └─────────────┘
```
💡**Lưu ý:**
- Dùng `new` khi cần ép buộc tạo đối tượng mới, ví dụ khi làm việc với dữ liệu nhập từ bàn phím, file, hoặc network.
- Tốn bộ nhớ hơn literal, chỉ nên dùng khi thật sự cần thiết.

---
### 2. Nối chuỗi
- Dùng toán tử `+` hoặc phương thức `concat()`. Java sẽ tạo **một chuỗi mới** chứa kết quả nối.

```java
String s3 = s1 + " " + s2;        // dùng toán tử +
String s4 = s1.concat(s2);        // dùng hàm concat()
```
---
### 3. Lấy độ dài chuỗi
- Dùng phương thức `length()` để lấy số lượng ký tự trong chuỗi.
```java
String text = "Hello";
System.out.println(text.length()); // 5
```
---
### 4. Lấy ký tự tại vị trí chỉ số
- Dùng `charAt(index)`.
- Index bắt đầu từ 0.
```java
String text = "Java";
System.out.println(text.charAt(0)); // J
System.out.println(text.charAt(3)); // a
```
---
### 5. Cắt chuỗi
- Dùng `substring(start, end)` để lấy phần chuỗi từ vị trí `start` đến `end - 1`.
```java
String text = "Hello";
System.out.println(text.substring(1, 4)); // ell
System.out.println(text.substring(2));    // llo
```
---
### 6. Chuyển đổi chữ hoa / chữ thường
- `toUpperCase()` → chuyển toàn bộ chuỗi thành chữ hoa.
- `toLowerCase()` → chuyển toàn bộ chuỗi thành chữ thường.
```java
String text = "Hello Java";
System.out.println(text.toUpperCase()); // HELLO JAVA
System.out.println(text.toLowerCase()); // hello java
```
---
