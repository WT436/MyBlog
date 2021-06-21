# How to format source code files (Cách định dạng file mã nguồn)

## Các quy tắc bắt buộc
- Một file code không quá 500 dòng
- Sử dụng dòng trắng để phân tách các phần độc lập trong code
- Các dòng code liên quan tới nhau nên đứng gần nhau
- Biến nên được định nghĩa gần nơi nó được sử dụng
- Biến cục bộ nên để ở đầu hàm
- Biến đối tượng nên được đặt ở đầu class
- Biến đếm của vòng lặp nên được định nghĩa bên trong vòng lặp
- Các hàm phụ thuộc nhau nên được đặt gần nhau
- Hàm gọi đứng trước hàm được gọi
- if/else/while/for khi có một dòng lệnh bên trong, vẫn phải xuống dòng và đặt dòng lệnh của nó trong ngoặc {}

## Phân loại Nội dung Diễn giải
* Cách định dạng file mã nguồn
Một file code không quá 500 dòng
Trung bình một class có số dòng là 200. Cho phép tối đa là 500 dòng. Thực tế cho thấy các dự án lớn, thành công trên thế giới có
trung bình là 200 dòng trong một file, và các dự án đó đã rất thành công. Ví dụ mã nguồn của: JUnit, Ant, Tomcat…
Do đó, không lý do gì ta có thể biện hộ cho việc một file code dài tới 2000 dòng được. Trong trường hợp đó cần tách ra thành các file
khác nhau với các ý nghĩa khác nhau.
* Sử dụng dòng trắng để phân tách các phần độc lập trong code
Sử dụng dòng trắng để phân tách các phần độc lập trong code: package/import/class/properties/function
* Các dòng code liên quan tới nhau nên đứng gần nhau 
Các dòng code trong cùng một hàm mà liên quan tới nhau nên đứng gần nhau (không được thêm dòng trắng vào giữa)
* Biến nên được định nghĩa gần nơi nó được sử dụng Các biến nên được định nghĩa gần nơi nó được sử dụng.
* Biến cục bộ nên để ở đầu hàm Trong trường hợp hàm nhỏ, biến cục bộ nên được định nghĩa ở đầu hàm.
* Biến đối tượng nên được đặt ở đầu class Biến đối tượng (instance variable) nên được đặt ở đầu class
* Biến đếm của vòng lặp nên được định nghĩa bên trong vòng lặp
Biến đếm của vòng lặp nên được định nghĩa bên trong vòng lặp.
* Các hàm phụ thuộc nhau nên được đặt gần nhau 
Các hàm phụ thuộc nhau nên được đặt gần nhau. Việc này sẽ giúp cho lập trình viên dễ dàng đọc và quản lý các hàm đó.
* Hàm gọi đứng trước hàm được gọi
Hàm gọi đứng trước hàm được gọi. Nguyên tắc đọc hàm là đọc từ trên xuống dưới: đọc hàm, trong hàm gọi tới hàm nào khác thì các hàm đó sẽ ở ngay phía dưới hàm này.
* if/else/while/for khi có một dòng lệnh bên trong, vẫn phải xuống dòng và đặt dòng lệnh của nó trong ngoặc {} 
Trường hợp if/else/while/for khi có một dòng lệnh bên trong, vẫn phải xuống dòng và đặt dòng lệnh của nó trong ngoặc {}.
Không được phép để cùng một dòng.
Ví dụ vi phạm: if(isValid) doSomeThing();
Hoặc:
if(isValid)
 doSomeThing();
Ví dụ hợp lệ (thêm { và } để bọc đoạn code trong if, kể cả trong đó có duy nhất 1 dòng code):
if(isValid){
 doSomeThing();
}