# Simplifying Conditional Expressions

Các điều kiện có xu hướng ngày càng trở nên phức tạp hơn trong logic của chúng theo thời gian, và vẫn có nhiều kỹ thuật hơn để chống lại điều này.

1. Decompose Conditional

Chúng ta có một câu lệnh điều kiện (if-then-else) phức tạp. Trích xuất các method từ điều kiện, sau đó một phần và các phần khác

2. Consolidate Conditional Expression

Chúng ta có một chuỗi các bài kiểm tra điều kiện với cùng một kết quả. Kết hợp chúng thành một biểu thức điều kiện duy nhất và trích xuất nó.

3. Consolidate Duplicate Conditional Fragments

Đoạn code giống nhau nằm trong tất cả các nhánh của biểu thức điều kiện. Di chuyển nó ra bên ngoài biểu thức.

4. Remove Control Flag

Chúng ta có một biến đang hoạt động như một cờ điều khiển cho một loạt các câu lệnh boolean. Thay vào đó, hãy sử dụng break or return.

5. Replace Nested Conditional with Guard Clauses

Một method có hành vi có điều kiện không làm rõ đường dẫn thực thi thông thường. Sử dụng các điều khoản bảo vệ cho tất cả các trường hợp đặc biệt.

6. Replace Conditiional with Polymorphsism 

Chúng ta có một điều kiện chọn hành vi khác nhau tùy thuộc vào loại object. Di chuyển từng phần của điều kiện sang một method ghi đè trong một class con. Làm cho method gốc trở nên trừu tượng.

7. Introduce Null Object

Chúng ta đã kiểm tra nhiều lần giá trị null. Thay thế giá trị null bằng một object null.

8. Introduce Assertion

Một phần code giả định điều gì đó về trạng thái của chương trình. Làm cho giả định rõ ràng với một khẳng định.

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>