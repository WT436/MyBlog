# Feature Envy (Tranh Chấp Chức Năng)

## Dấu hiệu Và Lý Do
- Một Method truy cập Data của một Object khác nhiều hơn dữ liệu của chính nó.
## Giải Quyết
- Theo nguyên tắc cơ bản, nếu mọi thứ thay đổi cùng một lúc, bạn nên giữ chúng ở vị trí cũ. Thông thường dữ liệu và chức năng sử dụng dữ liệu này được thay đổi cùng nhau (mặc dù có thể có ngoại lệ).
- Nếu một phương pháp rõ ràng nên được chuyển đến một nơi khác.
- Ít trùng lặp Code (nếu Code xử lý dữ liệu được đặt ở vị trí trung tâm).
- Tổ chức Code tốt hơn (các phương pháp xử lý dữ liệu bên cạnh dữ liệu thực tế).