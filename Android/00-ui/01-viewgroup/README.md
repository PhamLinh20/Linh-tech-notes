# 🟢 Android UI 

Phần **Android UI** là bước đầu tiên để làm quen với cách xây dựng giao diện trong ứng dụng Android.  
Ở đây mình sẽ học từ **những thành phần cơ bản nhất (View, ViewGroup)** cho đến **cách sắp xếp bố cục (Layout)** và **xử lý tương tác của người dùng**.

---

## 📚 Nội dung chính

### 1. Views  
- Các thành phần giao diện cơ bản: `TextView`, `Button`, `EditText`, `ImageView`, `CheckBox`, `RadioButton`, ...  
- Tạo View bằng **XML** và **code Java**  
- Thuộc tính quan trọng: `id`, `text`, `background`, `visibility`, `enabled`

---

### 2. ViewGroup  
- Khái niệm **container** – nơi chứa các View khác  
- Cấu trúc phân cấp giao diện (View Hierarchy)  
- Các loại ViewGroup thường dùng:  
  - `LinearLayout`  
  - `RelativeLayout`  
  - `ConstraintLayout`  
  - `FrameLayout`

---

### 3. Layout  
- Cách bố trí và sắp xếp thành phần trong màn hình  
- Các thuộc tính thường gặp:  
  - `layout_width`, `layout_height`  
  - `margin`, `padding`, `gravity`, `orientation`, `weight`  
- Tổ chức giao diện bằng **XML layout file**  
- Sử dụng **ConstraintLayout** để thiết kế linh hoạt và hiện đại hơn

---

### 4. Event Handling  
- Bắt sự kiện người dùng: `onClick`, `onLongClick`, `onTouch`, ...  
- Viết sự kiện bằng Java
