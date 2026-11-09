# Camm Car

Màn hình chính cho đầu Android ô tô và Samsung DeX.

- **Cột trái:** tên chủ xe, giờ, ngày, tốc độ GPS (km/h), số vệ tinh, 3 nút điều khiển (trước / phát-tạm dừng / sau).
- **Khung phải, chế độ Video:** chọn clip hoặc cả thư mục trong máy hay USB, phát ngay trong khung (ExoPlayer, hỗ trợ mp4, mkv, webm, mov, ts…). Có danh sách phát, lặp, trộn bài, toàn màn hình. Nhớ danh sách và vị trí đang xem cho lần mở sau.
- **Khung phải, chế độ YouTube:** YouTube bản điện thoại trong khung, tự thử lại khi mất mạng.
- **Dock dưới cùng:** ứng dụng đã ghim + nút mở tất cả ứng dụng (có ô tìm).

## Build ra APK

### Cách 1: GitHub (không cần cài gì)
1. Tạo repo mới trên github.com, tải toàn bộ thư mục này lên (giữ nguyên cấu trúc, gồm cả thư mục `.github`).
2. Vào tab **Actions**. Workflow "Build APK" tự chạy (khoảng 5 phút).
3. Mở lần chạy vừa xong, tải mục **CammCar-apk** ở cuối trang, giải nén ra file `app-release.apk`.

### Cách 2: Android Studio
1. Mở Android Studio → **Open** → chọn thư mục `CarLauncher`. Đợi Gradle sync xong.
2. Menu **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
3. File ra ở `app/build/outputs/apk/debug/app-debug.apk`.

APK được ký bằng khóa debug, cài trực tiếp được. Nếu máy báo xung đột chữ ký khi cập nhật, gỡ bản cũ rồi cài lại.

## Dùng

- **Đặt làm màn hình chính:** bấm Home → chọn Camm Car → Luôn dùng. Trên DeX, mở app như cửa sổ thường; kéo giãn cửa sổ thì bố cục tự đổi.
- **Thêm video:** chế độ Video → **＋ Chọn video** (chọn một hoặc nhiều file) hoặc **📁 Chọn thư mục** (lấy hết video trong thư mục, kể cả thư mục con, ví dụ thẻ nhớ / USB).
- **Toàn màn hình:** nút ⛶; thoát bằng ✕ góc trên trái hoặc nút Back.
- **Ghim ứng dụng:** nút lưới tròn xanh → giữ lâu một app. Giữ lâu app trong dock để bỏ ghim hoặc đổi thứ tự.
- **Tên chủ xe:** giữ lâu vào tên hoặc đồng hồ.

## Cấu trúc mã

| File | Nội dung |
|---|---|
| `app/src/main/java/vn/carlauncher/app/MainActivity.kt` | Toàn bộ màn hình: giờ, GPS, trình phát video, YouTube, dock, toàn màn hình |
| `app/src/main/java/vn/carlauncher/app/Apps.kt` | Đọc danh sách ứng dụng, adapter cho dock và lưới ứng dụng |
| `app/src/main/java/vn/carlauncher/app/Prefs.kt` | Lưu cài đặt, danh sách phát, app đã ghim |
| `app/src/main/res/layout/activity_main.xml` | Bố cục màn hình chính |
| `app/src/main/AndroidManifest.xml` | Quyền, khai báo launcher (HOME) và hỗ trợ DeX |
