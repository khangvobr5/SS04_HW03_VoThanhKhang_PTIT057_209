# BÁO CÁO BÀI TẬP 3: CẤU HÌNH XÁC THỰC SSH VÀ ĐẨY DỰ ÁN LÊN GITHUB

## 1. Thông Tin Chung
- **Bài tập**: Bài 3 - Cấu hình xác thực SSH và Đẩy dự án lên GitHub
- **Đường dẫn bài nộp**: `homework/session_04/ex3/`
- **Tài khoản GitHub**: `nguyenvantoan-code`
- **Email đăng ký**: `nguyenvantoan200608@gmail.com`
- **Repository URL (SSH)**: `git@github.com:nguyenvantoan-code/homework-session_04-ex3.git`
- **Repository URL (HTTPS)**: `https://github.com/nguyenvantoan-code/homework-session_04-ex3.git`

---

## 2. Quy Trình Thực Hiện

### Bước 1: Khởi tạo cặp khóa SSH Ed25519
Sử dụng thuật toán **Ed25519** bảo mật cao để tạo khóa SSH xác thực không cần mật khẩu:
```bash
ssh-keygen -t ed25519 -C "nguyenvantoan200608@gmail.com"
```
- Khóa private lưu tại: `~/.ssh/id_ed25519`
- Khóa public lưu tại: `~/.ssh/id_ed25519.pub`

Nội dung Khóa Public (`id_ed25519.pub`):
```text
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJqXJyfrSc4tWxRxbAxAn2dsRyNU9LDzwj/lSORlv3EK nguyenvantoan200608@gmail.com
```

---

### Bước 2: Thêm SSH Public Key vào Tài khoản GitHub
1. Sao chép nội dung tệp `~/.ssh/id_ed25519.pub`.
2. Truy cập GitHub: **Settings** -> **SSH and GPG keys** -> chọn **New SSH key**.
3. Nhập Title (ví dụ: `Personal Laptop Ed25519`) và dán chuỗi khóa public vào mục **Key**.
4. Nhấn **Add SSH key** để hoàn tất.

---

### Bước 3: Kiểm tra kết nối SSH tới GitHub
Chạy lệnh kiểm tra xác thực SSH với GitHub:
```bash
ssh -T git@github.com
```
**Kết quả thành công mong đợi**:
```text
Hi nguyenvantoan-code! You've successfully authenticated, but GitHub does not provide shell access.
```

---

### Bước 4: Khởi tạo Repository cục bộ và Cấu hình Remote SSH URL
Tại thư mục dự án cục bộ, tiến hành khởi tạo và cấu hình remote URL theo định dạng **SSH**:
```bash
# 1. Khởi tạo Git repository
git init

# 2. Cấu hình Remote URL bằng giao thức SSH (Ed25519)
git remote add origin git@github.com:nguyenvantoan-code/homework-session_04-ex3.git
```

Kiểm tra cấu hình Remote URL:
```bash
git remote -v
```
**Kết quả hiển thị**:
```text
origin  git@github.com:nguyenvantoan-code/homework-session_04-ex3.git (fetch)
origin  git@github.com:nguyenvantoan-code/homework-session_04-ex3.git (push)
```

---

### Bước 5: Tạo Commit và Đẩy mã nguồn lên GitHub
Thực hiện thêm tệp, tạo commit và đẩy nhánh `main` lên kho lưu trữ đám mây GitHub:
```bash
# Thêm tất cả các tệp vào Stage
git add .

# Tạo commit đầu tiên
git commit -m "first commit"

# Chuyển đổi tên nhánh chính thành main
git branch -M main

# Đẩy mã nguồn và thiết lập upstream tracking cho nhánh main
git push -u origin main
```

---

## 3. Tổng Kết Kết Quả Kiểm Tra

| Tiêu chí kiểm tra | Lệnh thực hiện | Kết quả mong đợi |
| :--- | :--- | :--- |
| **Xác thực SSH** | `ssh -T git@github.com` | Xác nhận thành công danh tính tài khoản GitHub |
| **Cấu hình Remote** | `git remote -v` | Định dạng `git@github.com:nguyenvantoan-code/homework-session_04-ex3.git` |
| **Push thành công** | `git push -u origin main` | Mã nguồn & commit history xuất hiện trên GitHub |
