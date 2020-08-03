Tạo đối tượng
Trong Chương trước có đề cập đến sự khác nhau giữa kiểu dữ liệu giá trị và kiểu dữ
liệu tham chiếu. Những kiểu dữ liệu chuẩn của C# như int, char, float,… là những kiểu
dữ liệu giá trị,và các biến được tạo ra từ các kiểu dữ liệu này được lưu trên stack. Tuy
nhiên, với các đối tượng kiểu dữ liệu tham chiếu thì được tạo ra trên heap, sử dụng từ
khóa new để tạo một đối tượng:

ThoiGian t = new ThoiGian();

t thật sự không chứa giá trị của đối tượng ThoiGian, nó chỉ chứa địa chỉ của đối tượng
được tạo ra trên heap, do vậy t chỉ chứa tham chiếu đến một đối tượng mà thôi.
Bộ khởi dựng

Thử xem lại ví dụ minh họa bài trước, câu lệnh tạo một đối tượng cho lớp ThoiGian
tương tự như việc gọi thực hiện một phương thức:

ThoiGian t = new ThoiGian();

Đúng như vậy, một phương thức sẽ được gọi thực hiện khi chúng ta tạo một đối tượng.
Phương thức này được gọi là bộ khởi dựng (constructor). Các phương thức này được
định nghĩa khi xây dựng lớp, nếu ta không tạo ra thì CLR sẽ thay mặt chúng ta mà tạo
phương thức khởi dựng một cách mặc định. Chức năng của bộ khởi dựng là tạo ra đối
tượng được xác định bởi một lớp và đặt trạng thái này hợp lệ. Trước khi bộ khởi dựng
được thực hiện thì đối tượng chưa được cấp phát trong bộ nhớ. Sau khi bộ khởi dựng
thực hiện hoàn thành thì bộ nhớ sẽ lưu giữ một thể hiện hợp lệ của lớp vừa khai báo.
Lớp ThoiGian trong ví dụ đó không định nghĩa bộ khởi dựng. Do không định nghĩa nên
trình biên dịch sẽ cung cấp một bộ khởi dựng cho chúng ta. Phương thức khởi dựng mặc
định được tạo ra cho một đối tượng sẽ không thực hiện bất cứ hành động nào, tức là
bên trong thân của phương thức rỗng. Các biến thành viên được khởi tạo các giá trị tầm
thường như thuộc tính nguyên có giá trị là 0 và chuỗi thì khởi tạo rỗng,..Bảng 4.2 sau
tóm tắt các giá trị mặc định được gán cho các kiểu dữ liệu cơ bản.

***********************

Thường thường, khi muốn định nghĩa một phương thức khởi dựng riêng ta phải cung
cấp các tham số để hàm khởi dựng có thể khởi tạo các giá trị khác ngoài giá trị mặc định
cho các đối tượng. Quay lại ví dụ 4.1 giả sử ta muốn truyền thời gian hiện hành: năm,
tháng, ngày,…để đối tượng có ý nghĩa hơn.

Để định nghĩa một bộ khởi dựng riêng ta phải khai báo một phương thức có tên giống
như tên lớp đã khai báo. Phương thức khởi dựng không có giá trị trả về và được khai
báo là public. Nếu phương thức khởi dựng này được truyền tham số thì phải khai báo
danh sách tham số giống như khai báo với bất kỳ phương thức nào trong một lớp. Ví dụ
1 được viết lại từ ví dụ bài trước và thêm một bộ khởi dựng riêng, phương phức khởi
dựng này sẽ nhận một tham số là một đối tượng kiểu DateTime do C# cung cấp.
Định nghĩa một bộ khởi dựng.

Khi phương thức này thực hiện

xong, một đối tượng ThoiGian được tạo ra và các biến của đối tượng cũng đã được khởi
tạo. Hàm ThoiGianHienHanh được gọi trong hàm Main() sẽ hiển thị giá trị thời gian lúc
đối tượng được tạo ra.

Chúng ta thử bỏ một số lệnh khởi tạo trong phương thức khởi dựng và cho thực hiện
chương trình lại thì các biến không được khởi tạo sẽ có giá trị mặc định là 0, do là biến
nguyên. Một biến thành viên kiểu nguyên sẽ được thiết lập giá trị là 0 nếu chúng ta
không gán nó trong phương thức khởi dựng. Chú ý rằng kiểu dữ liệu giá trị không thể
không được khởi tạo, nếu ta không khởi tạo thì trình biên dịch sẽ cung cấp các giá trị
mặc định theo bảng 1.

Ngoài ra trong chương trình trên có sử dụng đối tượng của lớp DateTime, lớp DateTime
này được cung cấp bởi thư viện System, lớp này cũng cung cấp các biến thành viên
public như: Year, Month, Day, Hour, Minute, và Second tương tự như lớp ThoiGian
của chúng ta. Thêm vào đó là lớp này có đưa ra một phương thức thành viên tĩnh tên là
Now, phương thức Now sẽ trả về một tham chiếu đến một thể hiện của một đối tượng
DateTime được khởi tạo với thời gian hiện hành. Theo như trên khi lệnh :

System.DataTime currentTime = System.DateTime.Now();

được thực hiện thì phương thức tĩnh Now() sẽ tạo ra một đối tượng DateTime trên bộ
nhớ heap và trả về một tham chiếu và tham chiếu này được gán cho biến đối tượng
currentTime.

Sau khi đối tượng currentTime được tạo thì câu lệnh tiếp theo sẽ thực hiện việc truyền
đối tượng currentTime cho phương thức khởi dựng để tạo một đối tượng ThoiGian:
ThoiGian t = new ThoiGian( currentTime );

Bên trong phương thức khởi dựng này tham số dt sẽ tham chiếu đến đối tượng DateTime
là đối tượng vừa tạo mà currentTime cũng tham chiếu. Nói cách khác lúc này tham số
dt và currentTime cùng tham chiếu đến một đối tượng DateTime trong bộ nhớ. Nhờ vậy
phương thức khởi dựng ThoiGian có thể truy cập được các biến thành viên public của
đối tượng DateTime được tạo trong hàm Main().

Có một sự nhấn mạnh ở đây là đối tượng DateTime được truyền cho bộ dựng ThoiGian
chính là đối tượng đã được tạo trong hàm Main và là kiểu dữ liệu tham chiếu. Do vậy
khi thực hiện truyền tham số là một kiểu dữ liệu tham chiếu thì con trỏ được ánh xạ qua
chứ hoàn toàn không có một đối tượng nào được sao chép lại.

Khởi tạo biến thành viên

Các biến thành viên có thể được khởi tạo trực tiếp khi khai báo trong quá trình khởi tạo,
thay vì phải thực hiện việc khởi tạo các biến trong bộ khởi dựng. Để thực hiện việc khởi
tạo này rất đơn giản là việc sử dụng phép gán giá trị cho một biến:

private int Giay = 30; // Khởi tạo

Việc khởi tạo biến thành viên sẽ rất có ý nghĩa, vì khi xác định giá trị khởi tạo như vậy
thì biến sẽ không nhận giá trị mặc định mà trình biên dịch cung cấp. Khi đó nếu các biến
này không được gán lại trong các phương thức khởi dựng thì nó sẽ có giá trị mà ta đã
khởi tạo. Ví dụ 4.4 minh họa việc khởi tạo biến thành viên khi khai báo. Trong ví dụ này
sẽ có hai bộ dựng ngoài bộ dựng mặc định mà trình biên dịch cung cấp, một bộ dựng
thực hiện việc gán giá trị cho tất cả các biến thành viên, còn bộ dựng thứ hai thì cũng
tương tự nhưng sẽ không gán giá trị cho biến Giay.

Minh hoạ sử dụng khởi tạo biến thành viên.

Nếu không khởi tạo giá trị của biến thành viên thì bộ khởi dựng mặc định sẽ khởi tạo
giá trị là 0 mặc định cho biến thành viên có kiểu nguyên. Tuy nhiên, trong trường hợp
này biến thành viên Giay được khởi tạo giá trị 30:

Giay = 30; // Khởi tạo

Trong trường hợp bộ khởi tạo thứ hai không truyền giá trị cho biến Giay nên biến này
vẫn lấy giá trị mà ta đã khởi tạo ban đầu là 30:

ThoiGian t2 = new ThoiGian(2001, 7, 3, 10, 5);
t2.ThoiGianHienHanh();

Ngược lại, nếu một giá trị được gán cho biến Giay như trong bộ khởi tạo thứ nhất thì giá
trị mới này sẽ được chồng lên giá trị khởi tạo.

Trong ví dụ trên lần đầu tiên tạo đối tượng ThoiGian do ta truyền vào đối tượng
DateTime nên hàm khởi dựng thứ nhất được thực hiện, hàm này sẽ gán giá trị 5 cho biến
Giay. Còn khi tạo đối tượng ThoiGian thứ hai, hàm khởi dựng thứ hai được thực hiện,
hàm này không gán giá trị cho biến Giay nên biến này vẫn còn lưu giữ lại giá trị 30 khi
khởi tạo ban đầu.

Bộ khởi dựng sao chép

Bộ khởi dựng sao chép thực hiện việc tạo một đối tượng mới bằng cách sao chép tất cả
các biến từ một đối tượng đã có và cùng một kiểu dữ liệu. Ví dụ chúng ta muốn đưa một
đối tượng ThoiGian vào bộ khởi dựng lớp ThoiGian để tạo một đối tượng ThoiGian mới
có cùng giá trị với đối tượng ThoiGian cũ. Hai đối tượng này hoàn toàn khác nhau và
chỉ giống nhau ở giá trị biến thành viên sao khi khởi dựng.

Ngôn ngữ C# không cung cấp bộ khởi dựng sao chép, do đó chúng ta phải tự tạo ra.
Việc sao chép các thành phần từ một đối tượng ban đầu cho một đối tượng mới như sau:
public ThoiGian( ThoiGian tg) { Nam = tg.Nam; Thang =
tg.Thang; Ngay = tg.Ngay; Gio = tg.Gio; Phut = tg.Phut;
Giay = tg.Giay; }

Khi đó ta có thể sao chép từ một đối tượng ThoiGian đã hiện hữu như sau:
ThoiGian t2 = new ThoiGian( t1 );

Trong đó t1 là đối tượng ThoiGian đã tồn tại, sau khi lệnh trên thực hiện xong thì đối
tượng t2 được tạo ra như bản sao của đối tượng t1.