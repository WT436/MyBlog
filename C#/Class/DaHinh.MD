Đa hình

Có hai cách thức khá mạnh để thực hiện việc kế thừa. Một là sử dụng lại mã nguồn, khi
chúng ta tạo ra lớp ListBox, chúng ta có thể sử dụng lại một vài các thành phần trong
lớp cơ sở như Window.

Tuy nhiên, cách sử dụng thứ hai chứng tỏ được sức mạnh to lớn của việc kế thừa đó là
tính đa hình (polymorphism). Theo tiếng Anh từ này được kết hợp từ poly là nhiều và
morph có nghĩa là form (hình thức). Do vậy, đa hình được hiểu như là khả năng sử dụng
nhiều hình thức của một kiểu mà không cần phải quan tâm đến từng chi tiết.
Khi một tổng đài điện thoại gởi cho máy điện thoại của chúng ta một tín hiệu có cuộc
gọi. 

Tổng đài không quan tâm đến điện thoại của ta là loại nào. Có thể ta đang dùng một
điện thoại cũ dùng motor để rung chuông, hay là một điện thoại điện tử phát ra tiếng
nhạc số. Hoàn toàn các thông tin về điện thoại của ta không có ý nghĩa gì với tổng đài,
tổng đài chỉ biết một kiểu cơ bản là điện thoại mà thôi và diện thoại này sẽ biết cách báo
chuông. Còn việc báo chuông như thế nào thì tổng đài không quan tâm. Tóm lại, tổng
đài chỉ cần bảo điện thoại hãy làm điều gì đó để reng. Còn phần còn lại tức là cách thức
reng là tùy thuộc vào từng loại điện thoại. Đây chính là tính đa hình.

Kiểu đa hình

Do một ListBox là một Window và một Button cũng là một Window, chúng ta mong
muốn sử dụng cả hai kiểu dữ liệu này trong tình huống cả hai được gọi là Window. Ví
dụ như trong một form giao diện trên MS Windows, form này chứa một tập các thể hiện
của Window. Khi form được hiển thị, nó yêu cầu tất cả các thể hiện của Window tự thực
hiện việc tô vẽ. Trong trường hợp này, form không muốn biết thành phần thể hiện là
loại nào như Button, CheckBox,...,. Điều quan trọng là form kích hoạt toàn bộ tập hợp
này tự thực hiện việc vẽ. Hay nói ngắn gọn là form muốn đối xử với những đối tượng
Window này một cách đa hình.

Phương thức đa hình

Để tạo một phương thức hỗ tính đa hình, chúng ta cần phải khai báo khóa virtual trong
phương thức của lớp cơ sở. Ví dụ, để chỉ định rằng phương thức DrawWindow() của
lớp Window trong ví dụ 5.1 là đa hình, đơn giản là ta thêm từ khóa virtual vào khai báo
như sau:

public virtual void DrawWindow()

Lúc này thì các lớp dẫn xuất được tự do thực thi các cách xử riêng của mình trong phiên
bản mới của phương thức DrawWindow(). Để làm được điều này chỉ cần thêm từ khóa
override để chồng lên phương thức ảo DrawWindow() của lớp cơ sở. Sau đó thêm các
đoạn mã nguồn mới vào phương thức viết chồng này.

Trong ví dụ minh họa 5.2 sau, lớp ListBox dẫn xụất từ lớp Window và thực thi một
phiên bản riêng của phương thức DrawWindow():

public override void DrawWindow() { base.DrawWindow();
Console.WriteLine("Writing string to the listbox: {0}",
listBoxContents); }

Từ khóa override bảo với trình biên dịch rằng lớp này thực hiện việc phủ quyết lại
phương thức DrawWindow() của lớp cơ sở. Tương tự như vậy ta có thể thực hiện việc
phủ quyết phương thức này trong một lớp dẫn xuất khác như Button, lớp này cũng được
dẫn xuất từ Window.

Trong phần thân của ví dụ 5.2, đầu tiên ta tạo ra ba đối tượng, đối tượng thứ nhất của
Window, đối tượng thứ hai của lớp ListBox và đối tượng cuối cùng của lớp Button. Sau
đó ta thực hiện việc gọi phương thức DrawWindow() cho mỗi đối tượng sau:

Window win = new Window( 1, 2 );
ListBox lb = new ListBox( 3, 4, "Stand alone list box");
Button b = new Button( 5, 6 );
win.DrawWindow();
lb.DrawWindow();
b.DrawWindow();

Đoạn chương trình trên thực hiện các công việc như yêu cầu của chúng ta, là từng đối
tượng thực hiện công việc tô vẽ của nó. Tuy nhiên, cho đến lúc này thì chưa có bất cứ
sự đa hình nào được thực thi. Mọi chuyện vẫn bình thường cho đến khi ta muốn tạo ra
một mảng các đối tượng Window, bởi vì ListBox cũng là một Window nên ta có thể tự
do đặt một đối tượng ListBox vào vị trí của một đối tượng Window trong mảng trên. Và
tương tự ta cũng có thể đặt một đối tượng Button vào bất cứ vị trí nào trong mảng các
đối tượng Window, vì một Button cũng là một Window.

Window[] winArray = new Window[3];
winArray[0] = new Window( 1, 2 );
winArray[1] = new ListBox( 3, 4, "List box is array");
winArray[2] = new Button( 5, 6 );
Chuyện gì xảy ra khi chúng ta gọi phương thức DrawWindow() cho từng đối tượng
trong mảng winArray.

for( int i = 0; i < 3 ; i++)
{
winAray[i].DrawWindow();
}

Trình biên dịch điều biết rằng có ba đối tượng Windows trong mảng và phải thực
hiện việc gọi phương thức DrawWindow() cho các đối tượng này. Nếu chúng ta không
đánh dấu phương thức DrawWindow() trong lớp Window là virtual thì phương thức
DrawWindow() trong lớp Window sẽ được gọi ba lần. Tuy nhiên do chúng ta đã đánh
dấu phương thức này ảo ở lớp cơ sở và thực thi việc phủ quyết phương thức này ỏ các
lớp dẫn xuất.

Khi ta gọi phương thức DrawWindow trong mảng, trình biên dịch sẽ dò ra được chính
xác kiểu dữ liệu nào được thực thi trong mảng khi đó có ba kiểu sẽ được thực thi là một
Window, một ListBox, và một Button. Và trình biên dịch sẽ gọi chính xác phương thức
của từng đối tượng. Đây là điều cốt lõi và tinh hoa của tính chất đa hình. Đoạn chương
trình hoàn chỉnh 5.2 minh họa cho sự thực thi tính chất đa hình.
Sử dụng phương thức ảo.

chúng ta đánh dấu một phương thức phủ quyết mới với từ khóa
phủ quyết override :

public override void DrawWindow()

Lúc này trình biên dịch biết cách sử dụng phương thức phủ quyết khi gặp đối tượng
mang hình thức đa hình. Trình biên dịch chịu trách nhiệm trong việc phân ra kiểu dữ
liệu thật của đối tượng để sau này xử lý. Do đó phương thức ListBox.DrawWindow() sẽ
được gọi khi một đối tượng Window tham chiếu đến một đối tượng thật sự là ListBox.

Từ khóa new và override

Trong ngôn ngữ C#, người lập trình có thể quyết định phủ quyết một phương thức ảo
bằng cách khai báo tường minh từ khóa override. Điều này giúp cho ta đưa ra một phiên
bản mới của chương trình và sự thay đổi của lớp cơ sở sẽ không làm ảnh hưởng đến
chương trình viết trong các lớp dẫn xuất. Việc yêu cầu sử dụng từ khóa override sẽ giúp
ta ngăn ngừa vấn đề này.

Bây giờ ta thử bàn về vấn đề này, giả sử lớp cơ sở Window của ví dụ trước được viết bởi
một công ty A. Cũng giả sử rằng lớp ListBox và RadioButton đươc viết từ những người
lập trình của công ty B và họ dùng lớp cơ sở Window mua được của công ty A làm lớp
cơ sở cho hai lớp trên. Người lập trình trong công ty B không có hoặc có rất ít sự kiểm
soát về những thay đổi trong tương lai với lớp Window do công ty A phát triển.
Khi nhóm lập trình của công ty B quyết định thêm một phương thức Sort( ) vào lớp
ListBox:

public class ListBox : Window { public virtual void Sort(
) {...} }

Việc thêm vào vẫn bình thường cho đến khi công ty A, tác giả của lớp cơ sở Window,
đưa ra phiên bản thứ hai của lớp Window. Và trong phiên bản mới này những người lập
trình của công ty A đã thêm một phương thức Sort( ) vào lớp cơ sở Window:

public class Window { //... public virtual void Sort( )
{...} }

Trong các ngôn ngữ lập trình hướng đối tượng khác như C++, phương thức ảo mới
Sort() trong lớp Window bây giờ sẽ hành động giống như là một phương thức cơ sở
cho phương thức ảo trong lớp ListBox. 

Trình biên dịch có thể gọi phương thức Sort( )
trong lớp ListBox khi chúng ta có ý định gọi phương thức Sort( ) trong Window. Trong
ngôn ngữ Java, nếu phương thức Sort( ) trong Window có kiểu trả về khác kiểu trả về
của phương thức Sort( ) trong lớp ListBox thì sẽ được báo lỗi là phương thức phủ quyết
không hợp lệ.

Ngôn ngữ C# ngăn ngừa sự lẫn lộn này, trong C# một phương thức ảo thì được xem như
là gốc rễ của sự phân phối ảo. Do vậy, một khi C# tìm thấy một phương thức khai báo
là ảo thì nó sẽ không thực hiện bất cứ việc tìm kiếm nào trên cây phân cấp kế thừa. Nếu
một phương thức ảo Sort( ) được trình bày trong lớp Window, thì khi thực hiện hành vi
của lớp Listbox không thay đổi.

Tuy nhiên khi biên dịch lại, thì trình biên dịch sẽ đưa ra một cảnh báo giống như sau:
…\class1.cs(54, 24): warning CS0114: ‘ListBox.Sort( )’ hides inherited member
‘Window.Sort()’.

To make the current member override that implementation, add the override keyword.
Otherwise add the new keyword.

Để loại bỏ cảnh báo này, người lập trình phải chỉ rõ ý định của anh ta. Anh ta có thể
đánh dấu phương thức ListBox.Sort( ) với từ khóa là new, và nó không phải phủ quyết
của bất cứ phương thức ảo nào trong lớp Window:

public class ListBox : Window { public new virtual Sort( )
{...} }

Việc thực hiện khai báo trên sẽ loại bỏ được cảnh báo. Mặc khác nếu người lập trình
muốn phủ quyết một phương thức trong Window, thì anh ta cần thiết phải dùng từ khóa
override để khai báo một cách tường minh:

public class ListBox : Window { public override void
Sort(){...} }
