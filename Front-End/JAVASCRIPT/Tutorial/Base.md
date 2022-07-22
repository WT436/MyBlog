# Khái niệm cơ bản

- JavaScript vay mượn hầu hết cú pháp của nó từ Java, C và C ++, nhưng nó cũng bị ảnh hưởng bởi Awk, Perl và Python.
- JavaScript phân biệt chữ hoa chữ thường và sử dụng bộ ký tự Unicode . Ví dụ, từ Früh (có nghĩa là "sớm" trong tiếng Đức) có thể được sử dụng làm tên biến.
- Trong JavaScript, các hướng dẫn được gọi là câu lệnh và được phân tách bằng dấu chấm phẩy (;).
- Dấu chấm phẩy là không cần thiết sau một câu lệnh nếu nó được viết trên dòng riêng của nó. Nhưng nếu bạn muốn có nhiều hơn một câu lệnh trên một dòng, thì chúng phải được phân tách bằng dấu chấm phẩy.

# biến

JavaScript có ba loại khai báo biến.

- var : Khai báo một biến, tùy chọn khởi tạo nó thành một giá trị.
- let : Khai báo một biến cục bộ, phạm vi khối, tùy chọn khởi tạo nó thành một giá trị.
- const : Khai báo một hằng số được đặt tên trong phạm vi khối, chỉ đọc.

### quy tắc khai báo

- Bạn sử dụng các biến làm tên tượng trưng cho các giá trị trong ứng dụng của mình. Tên của các biến, được gọi là định danh , tuân theo các quy tắc nhất định.
- Mã định danh JavaScript phải bắt đầu bằng một chữ cái, dấu gạch dưới ( \_) hoặc dấu đô la ( \$). Các ký tự tiếp theo cũng có thể là chữ số ( 0- 9).
- Vì JavaScript phân biệt chữ hoa chữ thường nên các chữ cái bao gồm các ký tự " A" đến " Z" (chữ hoa) cũng như " a" đến " z" (chữ thường).

### cách khai báo

- Bạn có thể khai báo một biến theo hai cách:
- Với từ khóa var. Ví dụ var x = 42,. Cú pháp này có thể được sử dụng để khai báo cả biến cục bộ và biến toàn cục, tùy thuộc vào ngữ cảnh thực thi .
- Với từ khóa consthoặc let. Ví dụ let y = 13,. Cú pháp này có thể được sử dụng để khai báo một biến cục bộ phạm vi khối. (Xem Phạm vi biến bên dưới.)
- Một biến được khai báo bằng cách sử dụng câu lệnh varor letkhông có giá trị được chỉ định nào có giá trị là undefined.

### kiểu dữ liệu và cấu trúc dữ liệu

1. Loại dữ liệu

- Tiêu chuẩn ECMAScript mới nhất xác định tám kiểu dữ liệu:
- null : Một từ khóa đặc biệt biểu thị một giá trị rỗng. (Vì JavaScript phân biệt chữ hoa chữ thường, null không giống với Null, NULL hoặc bất kỳ biến thể nào khác.)
- Boolean. true and false.
- undefined. : Thuộc tính cấp cao nhất có giá trị không được xác định.
- Number : Một số nguyên hoặc số dấu phẩy động. Ví dụ: 42 hoặc 3,14159.
- BigInt : Một số nguyên với độ chính xác tùy ý. Ví dụ: 9007199254740992n.
- String : Một chuỗi các ký tự đại diện cho một giá trị văn bản. Ví dụ: "Chào"
- Symbol: Một kiểu dữ liệu có các phiên bản là duy nhất và bất biến.
- Object

2. Chuyển đổi kiểu dữ liệu

- JavaScript là một ngôn ngữ được nhập động. Điều này có nghĩa là bạn không phải chỉ định kiểu dữ liệu của một biến khi bạn khai báo nó. Nó cũng có nghĩa là các kiểu dữ liệu được tự động chuyển đổi khi cần thiết trong quá trình thực thi tập lệnh.
- Vì JavaScript được nhập động, việc gán này không gây ra thông báo lỗi.

3. Số và toán tử '+'

- Trong các biểu thức liên quan đến giá trị số và chuỗi với toán tử +, JavaScript chuyển đổi các giá trị số thành chuỗi.

- Trong trường hợp giá trị đại diện cho một số nằm trong bộ nhớ dưới dạng chuỗi, có các phương pháp để chuyển đổi.
- parseInt()
- parseFloat()
