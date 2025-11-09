# 📝 Views trong Android

**View** là thành phần cơ bản nhất trong giao diện Android.  
Mọi thứ mà người dùng thấy hoặc tương tác trên màn hình (nút, ô nhập, hình ảnh, chữ, …) đều là **View** hoặc **con của View**.  

---

## 📄Khái niệm View
- View là lớp cơ sở (`android.view.View`) cho mọi thành phần UI.  
- Mỗi View chiếm một vùng hiển thị trên màn hình và có thể nhận tương tác từ người dùng.  
- Có thể hiển thị văn bản, hình ảnh, nhập liệu, nút bấm, các widget tương tác.  
---

## 🔑 Các View cơ bản
### 1. TextView
- Hiển thị văn bản trên màn hình.  
- Có thể định dạng font, màu, kích thước, kiểu chữ.

**XML**
```xml
<TextView
    android:id="@+id/tvHello"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Xin chào!"
    android:textSize="18sp"
    android:textColor="@color/black" />
```
### 2. EditText
- Ô nhập liệu cho phép người dùng gõ và chỉnh sửa văn bản (bằng bàn phím ảo hoặc phương thức khác).
- Dùng để thu thập dữ liệu từ người dùng, thường dùng trong form, ô tìm kiếm, hay nơi cần nhập thông tin.
- Có thể giới hạn kiểu dữ liệu (text, number, email, …) bằng inputType.

**XML**
```xml
<EditText
    android:id="@+id/etName"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:hint="Nhập tên của bạn" />
```
### 3. Button
- Nút bấm tương tác với người dùng, cho phép người dùng nhấn vào để thực hiện một hành động hoặc kích hoạt sự kiện.
- Có thể gắn sự kiện onClick trong XML hoặc Java.

**XML**
```xml
<Button
    android:id="@+id/btnSubmit"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Gửi" />
```

### 4. ImageView
- Hiển thị hình ảnh từ resource hoặc URL.
- Làm nền hoặc biểu tượng cho nút, thẻ, banner,..

**XML**
```xml
<ImageView
    android:id="@+id/imgLogo"
    android:layout_width="100dp"
    android:layout_height="100dp"
    android:src="@drawable/logo" />
```
### 5. CheckBox & RadioButton
- CheckBox cho phép người dùng chọn hoặc bỏ chọn một hoặc nhiều tùy chọn độc lập.
- RadioButton cho phép người dùng chỉ chọn được duy nhất 1 tùy chọn trong nhóm.

**XML**
```xml
<CheckBox
    android:id="@+id/cbAgree"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Tôi đồng ý" />

<RadioButton
    android:id="@+id/rbMale"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Nam" />

```
### 6. Switch
- Nút bật/tắt trạng thái.

**XML**
```xml
<Switch
    android:id="@+id/switchNotify"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Bật thông báo" />
```
---

## 🔎 Các thuộc tính cơ bản của View

| Thuộc tính |  Mô tả | Giá trị / Ví dụ |
|----------------|----------|--------------------|
| `android:id` | Định danh duy nhất cho mỗi View (dùng để truy cập trong Java/Kotlin) | `@+id/btnSubmit` |
| `android:layout_width` | Chiều rộng của View | `wrap_content` / `match_parent` / `100dp` |
| `android:layout_height` | Chiều cao của View | `wrap_content` / `match_parent` / `50dp` |
| `android:text` | Nội dung hiển thị (áp dụng cho TextView, Button, …) | `"Xin chào!"` |
| `android:hint` | Gợi ý văn bản trong ô nhập liệu (EditText) | `"Nhập tên..."` |
| `android:textColor` | Màu chữ hiển thị | `@color/black` / `#FF0000` |
| `android:textSize` | Kích thước chữ (đơn vị: sp) | `18sp` |
| `android:gravity` | Căn chỉnh nội dung bên trong View | `center` / `left` / `right` |
| `android:background` | Màu hoặc hình nền cho View | `@color/blue` / `@drawable/bg_button` |
| `android:visibility` | Trạng thái hiển thị của View | `visible` / `invisible` / `gone` |
| `android:enabled` | Cho phép hoặc vô hiệu hóa tương tác | `true` / `false` |
| `android:padding` | Khoảng cách **bên trong** giữa nội dung và biên View | `8dp`, `16dp` |
| `android:margin` | Khoảng cách **bên ngoài** giữa View và phần tử khác | `8dp`, `16dp` |




💡 **Ghi chú:**
- `wrap_content`: kích thước bằng đúng nội dung bên trong View.  

- `match_parent`: chiếm toàn bộ kích thước vùng chứa (ViewGroup cha). 

- `padding` : khoảng cách bên trong View (nội dung so với viền View).

- `margin`: khoảng cách bên ngoài View (viền View so với phần tử khác/cha).

- sp và dp (hay dip) là 2 đơn vị đo thường gặp, liên quan đến kích thước hiển thị và mật độ màn hình (dpi).
  - `dp` (density-independent pixel) Dùng để đo kích thước layout (chiều rộng, chiều cao, margin, padding…)

  - `sp` (scale-independent pixel) dùng cho kích thước chữ.  

