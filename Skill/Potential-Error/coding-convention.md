# Coding Convention 

* Coding conventions là một tập hợp các quy tắc được định nghĩa ra để quy ước quá trình code trong một dự án.
* Thường được xây dựng sau khi quá trình phân tích yêu cầu hệ thống, dựa vào các nhóm chức chức năng của một hệ thống.
* Project manager sẽ dựng một bộ khung Coding Conventions cho toàn dự án cũng như team leader có thể dựng lên từng bộ Coding Conventions cho team mình dựa trên bộ khung gốc.
* Nhờ có Coding conventions , những các thành viên trong dự án có thể hiểu đọc hiểu code của nhau dễ dàng hơn
* Thuận tiện hơn cho những developer khác khi họ tìm hiểu dự án các dự án cũ để phát triển thêm
Dựng lên một bộ quy tắc để thống nhất chung cho hệ thống hoặc dự án.
. . . . . . . 

## Naming rules (Quy tắc đặt tên)

* Pascal Case : Chữ cái đầu tiên trong từ định danh và chữ cái đầu tiên của mỗi từ nối theo sau phải được viết hoa. Sử dụng Pascal Case để đặt tên cho một tên có từ 3 ký tự trở lên.
* Camel Case : Chữ cái đầu tiên trong từ định danh là chữ thường và chữ cái đầu tiên của mối từ nối theo sau phải được viết hoa.
* Uppercase : Tất cả các ký tự trong từ định danh phải được viết hoa. Sử dụng quy tắc này đối với tên định danh có từ 2 ký tự trở xuống
. . . . . . . 

## Prefix a control (Tiền tố một số control)

* Bắt buộc đặt tên cho tất cả các control có tham gia xử lý dưới nền. Một số control được đặt theo kiểu Pascal với phần tiền tố đứng trước
. . . . . . . 

## Rules for distribution of source code (Quy định phân bố mã nguồn)

* Mỗi file mã nguồn chỉ chứa duy nhất một class. Tên class chính phải trùng với tên file mã nguồn.
* Với các kiểu enum, struct độc lập đơn giản ngoài class có thể được khai báo trong một file mã nguồn riêng hoặc trong file mã nguồn của class khác.
* Interface phải được khai báo trong một file mã nguồn riêng.

. . . . . . . 

## Command writing conventions (Quy ước viết câu lệnh)

* Mỗi câu lệnh riêng rẽ trên một dòng.
* Đối với biến kiểu bool, tránh dùng phép so sánh với true hoặc false.
. . . . . . 

## Source code block (Khối mã nguồn)

* Sử dụng cặp dấu { } để đánh dấu một khối mã nguồn. Mỗi dấu ngoặc nằm trên một dòng (Ngoại lệ, kiểu enum, thuộc tính gọn hoặc khởi tạo giá trị cho mảng có thể không cần).

* Trong các lệnh if, for, foreach, ... nếu chỉ có một lệnh thì có thể không cần đánh dấu khối mã nguồn. 

. . . . . . . 

## Indentation and spacing (Thụt đầu dòng và cách khoảng)
* Viết cách vào một khoảng tab đối với các lệnh nằm trong khối lệnh { }.
* Viết cách vào một khoảng tab đối với lệnh ngay sau if, else, while, for, foreach.
* Viết cách một khoảng trắng xung quanh các toán tử 2 ngôi và 3 ngôi.
* Viết cách một khoảng trắng sau dấu “,” và “;”

## Comment (Chú thích)
* Nên comment trên những đoạn code khó hiểu hoặc chức năng đặc biệt. Ngôn ngữ sử dụng để chú thích phải đồng bộ xuyên suốt chương trình. Chọn một trong hai ngôn ngữ: tiếng Việt Unicode có dấu hoặc tiếng Anh.

* Quy định chú thích:

    * Chỉ sử dụng // và /// để chú thích. Không dùng /* */.
    * Có chú thích trên đầu mỗi file source code mô tả chương trình, chức năng của chương trình, tác giả, v.v...
    * Khối xử lý dữ liệu: Có chú thích trên mỗi class, mỗi phương thức, mỗi thuộc tính của class mô tả chức năng, tham số, v.v...
    * Khối xử lý giao diện: Có chú thích mô tả chức năng trên mỗi phương thức không phải event, hàm Main.
* Các kiểu chú thích:

    * Đoạn code phức tạp
    * Mô tả trong thân hàm
    * Mô tả field
    * Đoạn code được người không phải tác giả sửa đổi