# 🧭 Layout trong Android

`Layout` là **thành phần quan trọng nhất trong giao diện Android**, chịu trách nhiệm **bố trí, sắp xếp và hiển thị các View** trên màn hình.  
Có thể hình dung `Layout` như **bộ khung (skeleton)** của giao diện – nơi mọi View (nút, văn bản, hình ảnh, input, v.v.) được đặt và định vị.

---

## 🧱 Khái niệm cơ bản

- Mỗi màn hình trong ứng dụng Android đều bắt đầu từ **một layout gốc (root layout)**.  
- Layout có thể **chứa các View hoặc các layout khác (ViewGroup)** → tạo ra **cấu trúc lồng nhau**.  

---
## 🧩 Các loại Layout phổ biến
### 1. Linear Layout
- Dùng để sắp xếp các View con theo một hướng — ngang (horizontal) hoặc dọc (vertical).
- LinearLayout = “bố trí thẳng hàng” các phần tử con
- Sử dụng khi bố cục đơn giản, ít thành phần

**Ví dụ:**

```xml
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="16dp">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome to Android!"
        android:textSize="18sp" />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Click me!" />

</LinearLayout>
```

Trong ví dụ trên:
- LinearLayout là layout cha, chứa hai View con (TextView, Button).
- Các phần tử được sắp theo chiều dọc (vertical) nhờ thuộc tính android:orientation.

---
### 2. Relative Layout
- Sắp xếp View dựa trên vị trí tương đối (ví dụ: “dưới TextView này”)
- Sử dụng khi cần bố trí phần tử linh hoạt nhưng chưa muốn dùng ConstraintLayout

**Lưu ý:** phải chỉ định vị trí tương đối (relative position) giữa các View để tránh hiện tượng các View bị chồng lên nhau do hệ thống không biết nên đặt cái nào ở đâu.

**Ví dụ:**

```xml
<RelativeLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <!-- View 1: nằm ở góc trên bên trái -->
    <TextView
        android:id="@+id/title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Title"
        android:textSize="18sp" />

    <!-- View 2: đặt BÊN PHẢI View title -->
    <EditText
        android:id="@+id/inputName"
        android:layout_width="150dp"
        android:layout_height="wrap_content"
        android:hint="Your name"
        android:layout_toRightOf="@id/title"
        android:layout_marginStart="16dp"/>

    <!-- View 3: đặt BÊN DƯỚI View title -->
    <Button
        android:id="@+id/btnSubmit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Submit"
        android:layout_below="@id/title"
        android:layout_marginTop="24dp"/>

</RelativeLayout>
```
Trong ví dụ trên:
- RelativeLayout là layout cha, cho phép sắp xếp các View dựa trên vị trí tương đối so với parent hoặc so với một View khác.
- EditText được đặt bên phải TextView nhờ android:layout_toRightOf="@id/title".
- Button được đặt bên dưới TextView nhờ android:layout_below="@id/title".
---
### 3. Constraint Layout
- Sắp xếp các View dựa trên ràng buộc (constraint) giữa:
    - View với View khác, hoặc
    - View với layout cha.
- “Constraint” nghĩa là ràng buộc vị trí.
- Mỗi View phải được “neo” vào ít nhất một cạnh ngang và một cạnh dọc để xác định vị trí của nó.
- Sử dụng khi thiết kế giao diện phức tạp, muốn hạn chế layout lồng nhau

**Ví dụ:**

```xml
<androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <!-- Title ở chính giữa ngang -->
    <TextView
        android:id="@+id/title"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Welcome!"
        android:textSize="20sp"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="32dp"/>

    <!-- Input nằm dưới Title và căn giữa -->
    <EditText
        android:id="@+id/inputName"
        android:layout_width="0dp"
        android:layout_height="wrap_content"
        android:hint="Enter your name"
        app:layout_constraintTop_toBottomOf="@id/title"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="24dp"
        android:layout_marginHorizontal="32dp"/>

    <!-- Button nằm dưới EditText + căn giữa ngang -->
    <Button
        android:id="@+id/btnSubmit"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Submit"
        app:layout_constraintTop_toBottomOf="@id/inputName"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        android:layout_marginTop="24dp"/>

</androidx.constraintlayout.widget.ConstraintLayout>
```
Trong ví dụ trên:

- ConstraintLayout là layout cha cho phép tạo ràng buộc linh hoạt giữa các View.
- TextView được căn giữa theo chiều ngang nhờ
layout_constraintStart_toStartOf="parent" và
layout_constraintEnd_toEndOf="parent".
- EditText được đặt bên dưới TextView nhờ layout_constraintTop_toBottomOf="@id/title" và được căn giữa nhờ ràng buộc hai bên vào parent.
-Button được đặt bên dưới EditText nhờ layout_constraintTop_toBottomOf="@id/inputName" và được căn giữa tương tự.
---

## 📝 Khi nào dùng loại Layout nào?
| Loại Layout        | Khi nào nên dùng?                                                | Ưu điểm                                           | Hạn chế                                      |
|--------------------|------------------------------------------------------------------|---------------------------------------------------|----------------------------------------------|
| **LinearLayout**   | Khi sắp xếp các View theo **1 chiều** (ngang hoặc dọc).          | Đơn giản, dễ dùng.                                | Giới hạn bố cục, dễ bị lồng nhiều cấp.       |
| **RelativeLayout** | Khi cần vị trí **tương đối** giữa các View.                     | Linh hoạt hơn LinearLayout.                       | Layout phức tạp → khó bảo trì.               |
| **ConstraintLayout** | Khi bố cục **phức tạp**, nhiều ràng buộc, ít nested layout (layout chồng nhau).   | Mạnh nhất, tối ưu hiệu năng, thay thế nhiều layout khác. | Học hơi khó (nhiều thuộc tính). |