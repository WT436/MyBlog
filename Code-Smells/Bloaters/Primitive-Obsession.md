# Primitive Obsession

- Sử dụng các nguyên thủy thay vì các đối tượng nhỏ cho các tác vụ đơn giản (chẳng hạn như tiền tệ, phạm vi, chuỗi đặc biệt cho số điện thoại, v.v.) (file common lib)
- Sử dụng hằng số để mã hoá thông tin (chẳng hạn như hằng số USER_ADMIN_ROLE = 1 để đề cập đến người dùng có quyền quản trị viên.)
- Sử dụng const chuỗi làm tên trường để sử dụng trong mảng dữ liệu.

## Vậy chúng ta phải ứng sử với nó như thế nào?
- Giống như hầu hết các mùi khác, những Primitive Obsession được sinh ra trong những khoảnh khắc yếu đuối. "Chỉ là một trường để lưu trữ một số dữ liệu!" lập trình viên cho biết.
Tạo một trường nguyên thủy dễ hơn nhiều so với tạo một lớp hoàn toàn mới, phải không? Và nó đã được thực hiện. Sau đó, một trường khác là cần thiết và được thêm vào theo cách tương tự. Này và kìa, Class trở nên khổng lồ và khó sử dụng.

## Trả đũa cho một Class có mùi khó chịu.
![image](https://user-images.githubusercontent.com/63473793/121805563-f47ced80-cc75-11eb-8888-f3d9c9f57757.png)
