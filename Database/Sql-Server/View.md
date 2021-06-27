# View

View là tập hợp các thủ tục chứa các đợn mã TSQL lưu trữ toàn bộ nội dung được định nghĩa trong view đó dưới dạng các query động thực sự .

- Why??
- mỗ loại csdl đều có đặc trưng quan trọng của nó chính vì vậy để giảm bơt các bảng lưu trữ các thông tin trong csdl người sử dụng tạo ra các câu query trung gian để lưu trữ ngay trung tâm để khi cần dữ liệu chúng ta có thể khai thác ngay mà không tốn bộ nhớ và thời gian thực thi để lưu trữ .
- view cx có những chức năng như DB là nó có thể chia sẻ nhiều mức khác nhau

cú pháp

```sql
CREATE VIEW tên AS
Câu truy vấn
```

- thực thi : SELECT \* FROM tên view

lưu ý :

- Câu lệnh SELECT được sử dụng để tạo khung nhìn không được bao gồm mệnh đề GROUP BY hoặc mệnh đề ORDER BY.
- Câu lệnh SELECT không được có từ khóa DISTINCT.
- View phải có tất cả các giá trị NOT NULL.
- không tạo view bằng cách sử dụng các truy vấn lồng nhau hoặc các truy vấn phức tạp.
- View nên được tạo từ một bảng duy nhất. Nếu chế độ xem được tạo bằng nhiều bảng thì chúng ta sẽ không được phép cập nhật chế độ xem.

- Xóa View DROP VIEW Tên View ;
- còn nữa chưa cập nhật :))
