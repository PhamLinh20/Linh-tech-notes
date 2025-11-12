# 🧩 ViewGroup trong Android

`ViewGroup` là thành phần đóng vai trò như **“cha”** của các `View`.   Nó chịu trách nhiệm **chứa, sắp xếp và quản lý bố cục (layout)** của các phần tử con trên giao diện.  
Trong Android, mọi layout như `LinearLayout`, `ConstraintLayout`, `FrameLayout`, `RelativeLayout`,… đều là lớp **con của ViewGroup** và mỗi loại ViewGroup có **cách sắp xếp View con khác nhau**.

---

## 🔎 Một số thuộc tính quan trọng của ViewGroup

| Thuộc tính | Ý nghĩa | Ghi chú |
|-------------|----------|---------|
| `android:orientation` | Hướng sắp xếp các View con (chỉ dùng cho `LinearLayout`) | `horizontal` hoặc `vertical` |
| `android:gravity` | Căn chỉnh nội dung bên trong ViewGroup | Ví dụ: `center`, `bottom`, `end` |
| `android:layout_gravity` | Căn chỉnh vị trí của ViewGroup trong phần tử cha | Thường dùng trong layout lồng nhau |
| `android:padding` | Khoảng cách **bên trong** ViewGroup, giữa viền và nội dung | Dùng để tạo không gian “thở” |
| `android:layout_margin` | Khoảng cách **bên ngoài** ViewGroup so với thành phần khác | Ảnh hưởng đến bố cục tổng thể |

---

## 📊 Phân biệt View và ViewGroup

| Tiêu chí | View | ViewGroup |
|-----------|-------|------------|
| **Vai trò** | Là **thành phần giao diện cơ bản** (nút bấm, văn bản, ảnh, input, …) | Là **container (bố cục)** chứa nhiều View hoặc ViewGroup khác |
| **Kế thừa từ** | `android.view.View` | `android.view.ViewGroup` (kế thừa `View`) |
| **Chức năng chính** | Hiển thị nội dung, nhận tương tác người dùng | Sắp xếp, định vị và quản lý các View con |
| **Ví dụ** | `TextView`, `Button`, `ImageView`, `EditText` | `LinearLayout`, `FrameLayout`, `ConstraintLayout` |
| **Có thể chứa View khác không?** | Không | Có |
| **Dùng khi** | Cần hiển thị một phần tử giao diện cụ thể | Cần tổ chức bố cục hoặc nhóm nhiều View |

---

## ⚙️ Ví dụ minh họa

```xml
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

   <Button
       android:id="@+id/button"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:text="Just a button"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toTopOf="parent" />


</androidx.constraintlayout.widget.ConstraintLayout>
```
---

## 💡 Ghi nhớ
- Mọi layout đều kế thừa từ ViewGroup.
- Có thể lồng nhiều ViewGroup, nhưng nên tránh quá phức tạp để đảm bảo hiệu năng.
- Dùng ConstraintLayout cho bố cục phức tạp – nó linh hoạt và tối ưu hơn.
- Hiểu rõ các thuộc tính của ViewGroup giúp bạn kiểm soát layout chính xác hơn.