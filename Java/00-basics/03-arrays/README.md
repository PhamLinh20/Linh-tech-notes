
# 🔢 Arrays (Mảng)

**Array (Mảng)** là cấu trúc dữ liệu dùng để **lưu trữ nhiều giá trị cùng kiểu dữ liệu** trong **một biến duy nhất**.  
- Giúp **quản lý dữ liệu hiệu quả**, thay vì khai báo nhiều biến lẻ tẻ.  
- Trong Java, mảng là **đối tượng**, có **kích thước cố định** (khai báo một lần, không thể thay đổi).  
- Các phần tử trong mảng được **đánh chỉ số (index)** bắt đầu từ **0**.

**Ví dụ:**
Một sàn thương mại điện tử dùng mảng để lưu các sản phẩm trong giỏ hàng của khách, thay vì tạo biến riêng cho từng sản phẩm.
Điều này giúp quản lý và tính toán tổng tiền nhanh và gọn hơn.

---
## ⚙️ Đặc điểm của mảng
- **Kiểu dữ liệu đồng nhất**: Tất cả các phần tử trong một mảng phải cùng một kiểu dữ liệu, có thể là kiểu nguyên thủy (như int, char,...) hoặc kiểu đối tượng (như String, Object,...). 
- **Kích thước cố định:** Khi mảng được khởi tạo, số lượng phần tử của nó là cố định và không thể thay đổi trong suốt quá trình chạy của chương trình. 
- **Lập chỉ mục:** Mỗi phần tử trong mảng được truy cập thông qua một chỉ số (index) dạng số nguyên. Chỉ số của phần tử đầu tiên luôn là 0, và tăng dần cho các phần tử tiếp theo. 
- **Bộ nhớ liên tiếp:** Các phần tử của mảng được lưu trữ trong các vị trí bộ nhớ liên tiếp, điều này góp phần vào khả năng truy cập nhanh của mảng. 

---
## ⚡ Các loại mảng
### 1. Mảng 1 chiều (1D Array)
- Đây là loại mảng cơ bản nhất, lưu trữ một danh sách các phần tử cùng kiểu dữ liệu theo **một hàng duy nhất**. 
- **Cú pháp:**
```java
dataType[] arrayName = new dataType[size];
```
- **Ví dụ:** Danh sách điểm thi của 5 học sinh.

| Index | 0   | 1   | 2   | 3   | 4   |
|------:|-----|-----|-----|-----|-----|
| Value | 8.5 | 9.0 | 7.5 | 6.0 | 8.0 |

---
### 2. Mảng 2 chiều (2D Array)
- Dùng để biểu diễn dữ liệu dạng bảng hoặc ma trận.
- **Cú pháp:**
```java
dataType[][] arrayName = new dataType[rows][columns];
```

- **Ví dụ:** Bảng điểm của 3 học sinh với 3 môn học.

|        | Toán | Lý  | Hóa |
|--------|-----:|----:|----:|
| **HS1**| 8.5  | 7.0 | 9.0 |
| **HS2**| 6.5  | 8.5 | 7.5 |
| **HS3**| 9.0  | 8.0 | 8.5 |

---
## 🛠️ Các thao tác thường gặp với mảng
### 1. Khởi tạo mảng (initialization)
Có 2 cách phổ biến để khởi tạo:

- Cách 1: Khởi tạo kích thước trước, gán giá trị sau
```java
int[] numbers = new int[5];  // Mảng 5 phần tử, mặc định = 0
```
- Cách 2: Khởi tạo và gán giá trị trực tiếp
```java
int[] numbers = {1, 2, 3, 4, 5};
``` 

💡 **Lưu ý:**
- Mảng trong Java chỉ chứa một kiểu dữ liệu duy nhất.
- Khi đã khởi tạo kích thước, không thể thay đổi độ dài.

---
### 2. Gán và truy cập phần tử
- Truy cập phần tử: Sử dụng chỉ số (index), bắt đầu từ 0.

- **Ví dụ:**
```java
int[] numbers = new int[3];
numbers[0] = 10; // Gán giá trị 10 cho phần tử đầu tiên
numbers[1] = 20; // Gán giá trị 20 cho phần tử thứ 2
numbers[2] = 30; // Gán giá trị 30 cho phần tử thứ 3

System.out.println(numbers[0]); // Truy cập và in ra 10
```

---
### 3. Duyệt mảng
- Duyệt mảng giúp xử lý từng phần tử, ví dụ tính tổng, tìm giá trị lớn nhất, in danh sách...
#### 3.1 Sử dụng vòng lặp for
- **Ví dụ:**

```java
int[] numbers = {1, 2, 3, 4, 5}; 
for (int i = 0; i < numbers.length; i++) { // numbers.length lấy độ dài của mảng
    System.out.println(numbers[i]); // In ra giá trị của phần tử tại vị trí i
```
#### 3.2 Sử dụng vòng lặp for-each (ngắn gọn hơn)
- **Ví dụ:**

```java
for (int num : numbers) { //Lấy từng số trong numbers, gán vào biến num 
    System.out.println(num); // In giá trị của num ra màn hình
}
```
#### 3.3 Duyệt mảng 2 chiều
- **Ví dụ:**

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

for (int i = 0; i < matrix.length; i++) { // Lặp qua từng dòng của ma trận
    for (int j = 0; j < matrix[i].length; j++) {  // Lặp qua từng phần tử trong dòng (cột)
        System.out.print(matrix[i][j] + " ");  // In phần tử tại dòng i, cột j
    }
    System.out.println();
}
```

---
## 📌 Ưu điểm và hạn chế
### 1. Ưu điểm 
- **Truy cập nhanh:** truy cập nhanh bằng chỉ số
- **Quản lý bộ nhớ dễ:** mảng có kích thước cố định nên việc quản lý bộ nhớ đơn giản, dễ dự đoán.
- **Tổ chức dữ liệu rõ ràng:** mảng giúp lưu trữ các phần tử liên quan cùng loại một cách có thứ tự và dễ quản lý.

---
### 2. Hạn chế
- **Kích thước cố định:** khi tạo mảng, kích thước không thể thay đổi, dễ bị lãng phí bộ nhớ hoặc thiếu chỗ nếu tính sai kích thước.
- **hỉ chứa cùng kiểu dữ liệu:** mảng chỉ lưu cùng loại dữ liệu, nên nếu cần nhiều loại dữ liệu thì phải xử lý phức tạp hơn.
- **Thao tác chèn/xóa khó:** thêm hoặc xóa phần tử giữa mảng tốn công vì phải dịch chuyển nhiều phần tử.


