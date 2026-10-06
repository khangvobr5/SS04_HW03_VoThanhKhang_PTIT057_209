# BÁO CÁO NỘP BÀI - SESSION 04 - EX 3

## Thông Tin Nộp Bài
- **Họ và tên / GitHub**: `nguyenvantoan-code`
- **Email**: `nguyenvantoan200608@gmail.com`
- **Bài tập**: Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub
- **Loại khóa SSH**: Ed25519 (`ssh-ed25519`)
- **Remote Repository URL (SSH)**: `git@github.com:nguyenvantoan-code/homework-session_04-ex3.git`

## Chi Tiết Các Bước Đã Thực Hiện
1. **Sinh khóa SSH Ed25519**: `ssh-keygen -t ed25519 -C "nguyenvantoan200608@gmail.com"`
2. **Cấu hình SSH Public Key**: Thêm public key (`~/.ssh/id_ed25519.pub`) vào tài khoản GitHub `nguyenvantoan-code`.
3. **Xác nhận kết nối SSH**: `ssh -T git@github.com`
4. **Cấu hình Git Remote SSH**: `git remote add origin git@github.com:nguyenvantoan-code/homework-session_04-ex3.git`
5. **Commit và Push**: `git commit -m "first commit"`, `git branch -M main`, `git push -u origin main`
