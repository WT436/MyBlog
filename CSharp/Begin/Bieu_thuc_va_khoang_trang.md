=============>Biểu thức và khoảng trắng

Biểu thức

Những câu lệnh mà thực hiện việc đánh giá một giá trị gọi là biểu thức. Một phép gán
một giá trị cho một biến cũng là một biểu thức:
var1 = 24;

Trong câu lệnh trên phép đánh giá hay định lượng chính là phép gán có giá trị là 24 cho
biến var1. Lưu ý là toán tử gán (‘=’) không phải là toán tử so sánh. Do vậy khi sử dụng
toán tử này thì biến bên trái sẽ nhận giá trị của phần bên phải. Các toán tử của ngôn
ngữ C# như phép so sánh hay phép gán sẽ được trình bày chi tiết trong mục toán tử của
chương này.

Do var1 = 24 là một biểu thức được định giá trị là 24 nên biểu thức này có thể được xem
như phần bên phải của một biểu thức gán khác:
var2 = var1 = 24;

Lệnh này sẽ được thực hiện từ bên phải sang khi đó biến var1 sẽ nhận được giá trị là 24
và tiếp sau đó thì var2 cũng được nhận giá trị là 24. Do vậy cả hai biến đều cùng nhận
một giá trị là 24. Có thể dùng lệnh trên để khởi tạo nhiều biến có cùng một giá trị như:
a = b = c = d = 24;

=============>Khoảng trắng (whitespace)

Trong ngôn ngữ C#, những khoảng trắng, khoảng tab và các dòng được xem như là
khoảng trắng (whitespace), giống như tên gọi vì chỉ xuất hiện những khoảng trắng để
đại diện cho các ký tự đó. C# sẽ bỏ qua tất cả các khoảng trắng đó, do vậy chúng ta có
thể viết như sau:
var1=24;
Hay
var1 = 24;
và trình biên dịch C# sẽ xem hai câu lệnh trên là hoàn toàn giống nhau.
Tuy nhiên lưu ý là khoảng trắng trong một chuỗi sẽ không được bỏ qua. Nếu chúng ta
viết:
System.WriteLine("Xin chao!");
mỗi khoảng trắng ở giữa hai chữ “Xin” và “chao” đều được đối xử bình thường như các
ký tự khác trong chuỗi.

Hầu hết việc sử dụng khoảng trắng như một sự tùy ý của người lập trình. Điều cốt yếu là
việc sử dụng khoảng trắng sẽ làm cho chương trình dễ nhìn dễ đọc hơn Cũng như khi ta
viết một văn bản trong MS Word nếu không trình bày tốt thì sẽ khó đọc và gây mất cảm
tình cho người xem. Còn đối với trình biên dịch thì việc dùng hay không dùng khoảng
trắng là không khác nhau.

Tuy nhiên, cũng cần lưu ý khi sử dụng khoảng trắng như sau:
int x = 24;
tương tự như:
int x=24;
nhưng không giống như:
intx=24;

Trình biên dịch nhận biết được các khoảng trắng ở hai bên của phép gán là phụ và có
thể bỏ qua, nhưng khoảng trắng giữa khai báo kiểu và tên biến thì không phải phụ hay
thêm mà bắt buộc phải có tối thiểu một khoảng trắng. Điều này không có gì bất hợp lý,
vì khoảng trắng cho phép trình biên dịch nhận biết được từ khoá int và không thể nào
nhận được intx.

Tương tự như C/C++, trong C# câu lệnh được kết thúc với dấu chấm phẩy ‘;’. Do vậy
có thể một câu lệnh trên nhiều dòng, và một dòng có thể nhiều câu lệnh nhưng nhất thiết
là hai câu lệnh phải cách nhau một dấu chấm phẩy.