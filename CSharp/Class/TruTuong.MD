Lớp trừu tượng

Mỗi lớp con của lớp Window nên thực thi một phương thức DrawWindow() cho riêng
mình. Tuy nhiên điều này không thực sự đòi hỏi phải thực hiện một cách bắt buộc. Để
yêu cầu các lớp con (lớp dẫn xuất) phải thực thi một phương thức của lớp cơ sở, chúng
ta phải thiết kế một phương thức một cách trừu tượng.

Một phương thức trừu tượng không có sự thực thi. Phương thức này chỉ đơn giản tạo ra
một tên phương thức và ký hiệu của phương thức, phương thức này sẽ được thực thi ở
các lớp dẫn xuất.

Những lớp trừu tượng được thiết lập như là cơ sở cho những lớp dẫn xuất, nhưng việc
tạo các thể hiện hay các đối tượng cho các lớp trừu tượng được xem là không hợp lệ.
Một khi chúng ta khai báo một phương thức là trừu tượng, thì chúng ta phải ngăn cấm
bất cứ việc tạo thể hiện cho lớp này.

Do vậy, nếu chúng ta thiết kế phương thức DrawWindow() như là trừu tượng trong lớp
Window, chúng ta có thể dẫn xuất từ lớp này, nhưng ta không thể tạo bất cứ đối tượng
cho lớp này. Khi đó mỗi lớp dẫn xuất phải thực thi phương thức DrawWindow(). Nếu
lớp dẫn xuất không thực thi phương thức trừu tượng của lớp cơ sở thì lớp dẫn xuất đó
cũng là lớp trừu tượng, và ta cũng không thể tạo các thể hiện của lớp này được.
Phương thức trừu tượng được thiết lập bằng cách thêm từ khóa abstract vào đầu của
phần định nghĩa phương thức, cú pháp thực hiện như sau:

abstract public void DrawWindow( );

Do phương thức không cần phần thực thi, nên không có dấu ({}) mà chỉ có dấu chấm
phẩy (;) sau phương thức. Như thế với phương thức DrawWindow() được thiết kế là
trừu tượng thì chỉ cần câu lệnh trên là đủ.

Nếu một hay nhiều phương thức được khai báo là trừu tượng, thì phần định nghĩa lớp
phải được khai báo là abstract, với lớp Window ta có thể khai báo là lớp trừu tượng như
sau:

abstract public void Window

Ví dụ sau minh họa việc tạo lớp Window trừu tượng và phương thức trừu tượng
DrawWindow() của lớp Window.

Trong ví dụ trên, lớp Window được khai báo là lớp trừu tượng và do vậy nên chúng ta
không thể tạo bất cứ thể hiện nào của lớp Window. Nếu chúng ta thay thế thành viên
đầu tiên của mảng:

winArray[0] = new ListBox( 1, 2, "First List Box");
bằng câu lệnh sau:
winArray[0] = new Window( 1, 2);

Thì trình biên dịch sẽ báo một lỗi như sau:

Cannot create an instance of the abstract class or interface ‘Window’

Chúng ta có thể tạo được các thể hiện của lớp ListBox và Button, bởi vì hai lớp này đã
phủ quyết phương thức trừu tượng. Hay có thể nói hai lớp này đã được xác định (ngược
với lớp trừu tượng).

Hạn chế của lớp trừu tượng

Mặc dù chúng ta đã thiết kế phương thức DrawWindow() như một lớp trừu tượng để hỗ
trợ cho tất cả các lớp dẫn xuất được thực thi riêng, nhưng điều này có một số hạn chế.
Nếu chúng ta dẫn xuất một lớp từ lớp ListBox như lớp DropDownListBox, thì lớp này
không được hỗ trợ để thực thi phương thức DrawWindow( ) cho riêng nó.

Khác với ngôn ngữ C++, trong C# phương thức Window.DrawWindow( ) không thể
cung cấp một sự thực thi, do đó chúng ta sẽ không thể lấy được lợi ích của phương
thức DrawWindow() bình thường dùng để chia xẻ bởi các lớp dẫn xuất.

Cuối cùng những lớp trừu tượng không có sự thực thi căn bản; chúng thể hiện ý tưởng
về một sự trừu tượng, điều này thiết lập một sự giao ước cho tất cả các lớp dẫn xuất. Nói
cách khác các lớp trừu tượng mô tả một phương thức chung của tất cả các lớp được thực
thi một cách trừu tượng.

Ý tưởng của lớp trừu tượng Window thể hiện những thuộc tính chung cùng với những
hành vi của tất cả các Window, thậm chí ngay cả khi ta không có ý định tạo thể hiện của
chính lớp trừu tượng Window.

Ý nghĩa của một lớp trừu tượng được bao hàm trong chính từ “trừu tượng”. Lớp này
dùng để thực thi một “Window” trừu tượng, và nó sẽ được biểu lộ trong các thể hiện xác
định của Windows, như là Button, ListBox, Frame,...

Các lớp trừu tượng không thể thực thi được, chỉ có những lớp xác thực tức là những lớp
dẫn xuất từ lớp trừu tượng này mới có thể thực thi hay tạo thể hiện. Một sự thay đổi việc
sử dụng trừu tượng là định nghĩa một giao diện (interface), phần này sẽ được trình bày
trong Chương 8 nói về giao diện.

Lớp cô lập (sealed class)

Ngược với các lớp trừu tượng là các lớp cô lập. Một lớp trừu tượng được thiết kế cho
các lớp dẫn xuất và cung cấp các khuôn mẫu cho các lớp con theo sau. Trong khi một
lớp cô lập thì không cho phép các lớp dẫn xuất từ nó. Để khai báo một lớp cô lập ta
dùng từ khóa sealed đặt trước khai báo của lớp không cho phép dẫn xuất. Hầu hết các
lớp thường được đánh dấu sealed nhằm ngăn chặn các tai nạn do sự kế thừa gây ra.
Nếu khai báo của lớp Window trong ví dụ 5.3 được thay đổi từ khóa abstract bằng
từ khóa sealed (cũng có thể loại bỏ từ khóa trong khai báo của phương thức
DrawWindow()). Chương trình sẽ bị lỗi khi biên dịch. Nếu chúng ta cố thử biên dịch
chương trình thì sẽ nhận được lỗi từ trình biên dịch:

‘ListBox’ cannot inherit from sealed class ‘Window’
Đây chỉ là một lỗi trong số những lỗi như ta không thể tạo một phương thức thành viên
protected trong một lớp khai báo là sealed.

Gốc của tất cả các lớp: Lớp Object

Tất cả các lớp của ngôn ngữ C# của bất cứ kiểu dữ liệu nào thì cũng được dẫn xuất từ
lớp System.Object. Thú vị là bao gồm cả các kiểu dữ liệu giá trị.

Một lớp cơ sở là cha trực tiếp của một lớp dẫn xuất. Lớp dẫn xuất này cũng có thể làm
cơ sở cho các lớp dẫn xuất xa hơn nữa, việc dẫn xuất này sẽ tạo ra một cây thừa kế hay
một kiến trúc phân cấp. Lớp gốc là lớp nằm ở trên cùng cây phân cấp thừa kế, còn các
lớp dẫn xuất thì nằm bên dưới. Trong ngôn ngữ C#, lớp gốc là lớp Object, lớp này nằm
trên cùng trong cây phân cấp các lớp.

Lớp Object cung cấp một số các phương thức dùng cho các lớp dẫn xuất có thể thực
hiện việc phủ quyết. Những phương thức này bao gồm Equals() kiểm tra xem hai đối
tượng có giống nhau hay không. Phương thức GetType() trả về kiểu của đối tượng. Và
phương thức ToString() trả về một chuỗi thể hiện lớp hiện hành. Sau đây là bảng tóm
tắt các phương thức của lớp Object.

Equal( ) So sánh bằng nhau giữa hai đối tượng
GetHashCode( ) Cho phép những đối tượng cung cấp riêngnhững hàm băm cho
sử dụng tập hợp.
GetType( ) Cung cấp kiểu của đối tượng
ToString( ) Cung cấp chuỗi thể hiện của đối tượng
Finalize( ) Dọn dẹp các tài nguyên
MemberwiseClone(
)

Tạo một bản sao từ đối tượng.
Ví dụ sau minh họa việc sử dụng phương thức ToString( ) thừa kế từ lớp Object.
Thừa kế từ Object.

-----------------------------------------------------------------------------

Trong tài liệu của lớp Object phương thức ToString() được khai báo như sau:
public virtual string ToString();

Đây là phương thức ảo public, phương thức này trả về một chuỗi và không nhận tham
số. Tất cả kiểu dữ liệu được xây dựng sẵn, như kiểu int, dẫn xuất từ lớp Object nên nó
cũng có thể thực thi các phương thức của lớp Object.

Lớp SomeClass trong ví dụ trên thực hiện việc phủ quyết phương thức ToString(), do đó
phương thức này sẽ trả về giá trị có nghĩa. Nếu chúng ta không phủ quyết phương thức
ToString() trong lớp SomeClass, phương thức của lớp cơ sở sẽ được thực thi, và kết quả
xuất ra sẽ có thay đổi như sau:

The value of s is SomeClass

Như chúng ta thấy, hành vi mặc định đã trả về một chuỗi chính là tên của lớp đang thể
hiện.

Các lớp không cần phải khai báo tường minh việc dẫn xuất từ lớp Object, việc kế thừa
sẽ được đưa vào một cách ngầm định. Như lớp SomeClass trên ta không khai báo bất cứ
dẫn xuất của lớp nào nhưng C# sẽ tự động đưa lớp Object thành lớp dẫn xuất. Do đó ta
mới có thể phủ quyết phương thức ToString() của lớp Object.
