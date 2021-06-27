# Biến và hằng

Để tạo một biến chúng ta phải khai báo kiểu của biến và gán cho biến một tên duy nhất.
Biến có thể được khởi tạo giá trị ngay khi được khai báo, hay nó cũng có thể được gán
một giá trị mới vào bất cứ lúc nào trong chương trình. Ví dụ sau minh họa sử dụng biến.
Khởi tạo và gán giá trị đến một biến.

```c#
class MinhHoaC3
{
    static void Main()
    {
        int bien1 = 9;
        System.Console.WriteLine("Sau khi khoi tao: bien1 ={0}",bien1);
        bien1 = 15;
        System.Console.WriteLine("Sau khi gan: bien1 ={0}", bien1);
    }
}
```

```
Kết quả:
Sau khi khoi tao: bien1 = 9
Sau khi gan: bien1 = 15
```

Ngay khi khai báo biến ta đã gán giá trị là 9 cho biến, khi xuất biến này thì biến có giá
trị là 9. Thực hiện phép gán biến cho giá trị mới là 15 thì biến sẽ có giá trị là 15 và xuất
kết quả là 15.

## Gán giá trị xác định cho biến

C# đòi hỏi các biến phải được khởi tạo trước khi được sử dụng. Để kiểm tra luật này
chúng ta thay đổi dòng lệnh khởi tạo biến bien1 trong ví dụ 3.1 như sau:
int bien1;

và giữ nguyên phần còn lại ta được ví dụ sau:
Sử dụng một biến không khởi tạo.

```c#
class MinhHoaC3
{
    static void Main()
    {
        int bien1 = 9;
        System.Console.WriteLine("Sau khi khoi tao: bien1 ={0}",bien1);
        bien1 = 15;
        System.Console.WriteLine("Sau khi gan: bien1 ={0}", bien1);
    }
}
```

Khi biên dịch đoạn chương trình trên thì trình biên dịch C# sẽ thông báo một lỗi sau:
...error CS0165: Use of unassigned local variable ‘bien1’
Việc sử dụng biến khi chưa được khởi tạo là không hợp lệ trong C#. Ví dụ 2 trên không
hợp lệ.

Tuy nhiên không nhất thiết lúc nào chúng ta cũng phải khởi tạo biến. Nhưng để dùng
được thì bắt buộc phải gán cho chúng một giá trị trước khi có một lệnh nào tham chiếu
đến biến đó. Điều này được gọi là gán giá trị xác định cho biến và C# bắt buộc phải thực
hiện điều này.Ví dụ sau minh họa một chương trình đúng.

## Hằng

Hằng cũng là một biến nhưng giá trị của hằng không thay đổi. Biến là công cụ rất mạnh,
tuy nhiên khi làm việc với một giá trị được định nghĩa là không thay đổi, ta phải đảm bảo
giá trị của nó không được thay đổi trong suốt chương trình. Ví dụ, khi lập một chương
trình thí nghiệm hóa học liên quan đến nhiệt độ sôi, hay nhiệt độ đông của nước, chương
trình cần khai báo hai biến là DoSoi và DoDong, nhưng không cho phép giá trị của hai
biến này bị thay đổi hay bị gán. Để ngăn ngừa việc gán giá trị khác, ta phải sử dụng biến
kiểu hằng.

Hằng được phân thành ba loại: 
- giá trị hằng (literal)
- biểu tượng hằng (symbolic constants)
- kiểu liệu kê (enumerations).

Giá trị hằng: ta có một câu lệnh gán như sau: x = 100;

Giá trị 100 là giá trị hằng. Giá trị của 100 luôn là 100. Ta không thể gán giá trị khác cho
100 được.

Biểu tượng hằng: gán một tên cho một giá trị hằng, để tạo một biểu tượng hằng dùng từ
khóa const và cú pháp sau:

<const> <type> <tên hằng> = <giá trị>;

Một biểu tượng hằng phải được khởi tạo khi khai báo, và chỉ khởi tạo duy nhất một lần
trong suốt chương trình và không được thay đổi.

const int DoSoi = 100;

Trong khai báo trên, 32 là một hằng số và DoSoi là một biểu tượng hằng có kiểu nguyên.
Ví dụ sau minh họa việc sử dụng những biểu tượng hằng.

## Sử dụng biểu tượng hằng.


```c#
class MinhHoaC3
{
    static void Main()
    {
    const int DoSoi = 100; // Độ C
    const int DoDong = 0; // Độ C
    System.Console.WriteLine( "Do dong cua nuoc {0}", DoDong );
    System.Console.WriteLine( "Do soi cua nuoc {0}", DoSoi );
    }
}
```

```
Kết quả:
Do dong cua nuoc 0
Do soi cua nuoc 100
```

Ví dụ trên tạo ra hai biểu tượng hằng chứa giá trị nguyên: DoSoi và DoDong, theo qui
tắc đặt tên hằng thì tên hằng thường được đặt theo cú pháp Pascal, nhưng điều này không
đòi hỏi bởi ngôn ngữ nên ta có thể đặt tùy ý.

Việc dùng biểu thức hằng này sẽ làm cho chương trình được viết tăng thêm phần ý nghĩa
cùng với sự dễ hiểu. Thật sự chúng ta có thể dùng hằng số là 0 và 100 thay thế cho hai
biểu tượng hằng trên, nhưng khi đó chương trình không được dễ hiểu và không được tự
nhiên lắm. Trình biên dịch không bao giờ chấp nhận một lệnh gán giá trị mới cho một
biểu tượng hằng.

Khi đó trình biên dịch sẽ phát sinh một lỗi sau:
error CS0131: The left-hand side of an assignment must be a variable, property or
indexer

## Kiểu liệt kê

Kiểu liệt kê đơn giản là tập hợp các tên hằng có giá trị không thay đổi (thường được gọi
là danh sách liệt kê).

Trong ví dụ trên, có hai biểu tượng hằng có quan hệ với nhau:
const int DoDong = 0;
const int DoSoi = 100;

Do mục đích mở rộng ta mong muốn thêm một số hằng số khác vào danh sách trên, như
các hằng sau:

const int DoNong = 60; const int DoAm = 40; const int
DoNguoi = 20;

Các biểu tượng hằng trên điều có ý nghĩa quan hệ với nhau, cùng nói về nhiệt độ của
nước,khi khai báo từng hằng trên có vẻ cồng kềnh và không được liên kết chặt chẽ cho
lắm. Thay vào đó C# cung cấp kiểu liệt kê để giải quyết vấn đề trên:

```c#
enum NhietDoNuoc
{
DoDong = 0,
DoNguoi = 20,
DoAm = 40,
DoNong = 60,
DoSoi =100,
}
```

Mỗi kiểu liệt kê có một kiểu dữ liệu cơ sở, kiểu dữ liệu có thể là bất cứ kiểu dữ liệu
nguyên nào như int, short, long... tuy nhiên kiểu dữ lịêu của liệt kê không chấp nhận
kiểu ký tự. Để khai báo một kiểu liệt kê ta thực hiện theo cú pháp sau:

[thuộc tính] [bổ sung] enum <tên liệt kê> [:kiểu cơ sở]
{danh sách các thành phần liệt kê};

Thành phần thuộc tính và bổ sung là tự chọn sẽ được trình bày trong phần sau của sách.
Trong phần này chúng ta sẽ tập trung vào phần còn lại của khai báo. Một kiểu liệt kê bắt
đầu với từ khóa enum, tiếp sau là một định danh cho kiểu liệt kê:

enum NhietDoNuoc

Thành phần kiểu cơ sở chính là kiểu khai báo cho các mục trong kiểu liệt kê. Nếu bỏ qua
thành phần này thì trình biên dịch sẽ gán giá trị mặc định là kiểu nguyên int, tuy nhiên
chúng ta có thể sử dụng bất cứ kiểu nguyên nào như ushort hay long,..ngoại trừ kiểu ký
tự. Đoạn ví dụ sau khai báo một kiểu liệt kê sử dụng kiểu cơ sở là số nguyên không dấu
uint:

```c#
enum KichThuoc :uint
{
Nho = 1, Vua = 2, Lon = 3,
}
```

Là khai báo một kiểu liệt kê phải kết thúc bằng một danh sách liệt kê, danh sách liệt kê
này phải có các hằng được gán, và mỗi thành phần phải phân cách nhau dấu phẩy.
Ta viết lại ví dụ minh họa trên như sau.

Mỗi thành phần trong kiểu liệt kê tương ứng với một giá trị số, trong trường hợp này là
một số nguyên. Nếu chúng ta không khởi tạo cho các thành phần này thì chúng sẽ nhận
các giá trị tiếp theo với thành phần đầu tiên là 0.
Ta xem thử khai báo sau:

```c#
enum Thutu
{
ThuNhat, ThuHai, ThuBa = 10, ThuTu
}
```

Khi đó giá trị của ThuNhat là 0, giá trị của ThuHai là 1, giá trị của ThuBa là 10 và giá
trị của ThuTu là 11.

Kiểu liệt kê là một kiểu hình thức do đó bắt buộc phải thực hiện phép chuyển đổi tường
minh với các kiêu giá trị nguyên:

int x = (int) ThuTu.ThuNhat;

## Kiểu chuỗi ký tự

Kiểu dữ liệu chuỗi khá thân thiện với người lập trình trong bất cứ ngôn ngữ lập trình
nào, kiểu dữ liệu chuỗi lưu giữ một mảng những ký tự.

Để khai báo một chuỗi chúng ta sử dụng từ khoá string tương tự như cách tạo một thể
hiện của bất cứ đối tượng nào:

string chuoi;

Một hằng chuỗi được tạo bằng cách đặt các chuỗi trong dấu nháy đôi:
“Xin chao”

Đây là cách chung để khởi tạo một chuỗi ký tự với giá trị hằng:

string chuoi = "Xin chao"

Kiểu chuỗi sẽ được đề cập sâu trong chương 10.

## Định danh

Định danh là tên mà người lập trình chỉ định cho các kiểu dữ liệu, các phương thức,
biến, hằng, hay đối tượng.... Một định danh phải bắt đầu với một ký tự chữ cái hay dấu
gạch dưới, các ký tự còn lại phải là ký tự chữ cái, chữ số, dấu gạch dưới.
Theo qui ước đặt tên của Microsoft thì đề nghị sử dụng cú pháp lạc đà (camel notation)
bắt đầu bằng ký tự thường để đặt tên cho các biến là cú pháp Pascal (Pascal notation)
với ký tự đầu tiên hoa cho cách đặt tên hàm và hầu hết các định danh còn lại. Hầu
như Microsoft không còn dùng cú pháp Hungary như iSoNguyen hay dấu gạch dưới
Bien_Nguyen để đặt các định danh.

Các định danh không được trùng với các từ khoá mà C# đưa ra, do đó chúng ta không
thể tạo các biến có tên như class hay int được. Ngoài ra, C# cũng phân biệt các ký tự
thường và ký tự hoa vì vậy C# xem hai biến bienNguyen và bienguyen là hoàn toàn khác
nhau.

