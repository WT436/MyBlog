# Lớp thao tác tập tin

- Một lớp tập tin tồn tại bên trong lớp cơ sở gọi là File, lớp này được định vị bên trong namespace System.OI. Lớp File chứa một số các phương thức tĩnh được sử dụng để thao tác trên tập tin. Thật vậy, tất cả các phương thức bên trong lớp File điều là tĩnh. Bảng sau liệt kê những phương thức chính của lớp File

- AppendText Nối văn bản vào trong một tập tin
- Copy Tạo ra một tập tin mới từ tập tin hiện hữu
- Create Tạo ra một tập tin mới ở một vị trí xác định
- CreateText Tạo ra tập tin lưu giữ text
- Delete Xóa tập tin ở vị trí xác định. Tập tin phải hiện hữunếu không sẽ phát sinh ra ngoại lệ.
- Exists Kiểm tra xem tập tin có thực sự hiện hữu ở vị trí nàođó.
- GetAttributes Lấy thông tin thuộc tính của tập tin. Thông tin này bao gồm: tập tin có bị nén hay không, tên thư mục, cóthuộc tính ẩn, thuộc tính chỉ đọc, tập tin hệ thống...
- GetCreationTime Trả về ngày giờ tập tin được tạo ra
- GetLastAccessTime Trả về ngày giờ tập tin được truy cập lần cuối
- GetLastWriteTime Trả về ngày giờ tập tin được viết lần cuối
- Move Cho phép tập tin được di chuyển vào vị trí mới và đổi tên tập tin.
- Open Mở một tập tin tại vị trí đưa ra. Bằng việc mở tập tin này chúng ta có thể viết thông tin hay đọc thông tin từ nó.
- OpenRead Mở một tập tin hiện hữu để đọc
- OpenText Mở một tập tin để đọc dạng text
- OpenWrite Mở một tập tin xác định để viết
- SetAttributes Thiết lập thuộc tính cho tập tin
- SetCreationTime Thiết lập ngày giờ tạo tập tin
- SetLastAccessTime Thiết lập lại ngày giờ mà tập tin được truy cập lầncuối
- SetLastWriteTime Thiết lập ngày giờ mà tập tin được cập nhật lần cuối.

```c#
namespace Programming_CSharp
{
using System; using System.IO; public class Tester
{
public static void Main()
{
string[] CLA = Environment.GetCommandLineArgs();
if ( CLA.Length < 3)
{
Console.WriteLine("Format: {0} orig-file new-file",
CLA[0]);
}
else
{
string origfile = CLA[1];
string newfile = CLA[2];
Console.Write("Copy...");
try
{
File.Copy(origfile, newfile);
}
catch (System.IO.FileNotFoundException)
{
Console.WriteLine("\n{0} does not exist!", origfile);
return;
}
catch (System.IO.IOException)
{
Console.WriteLine("\n{0} already exist!", newfile);
return;
}
catch (Exception e)
{
Console.WriteLine("\nAn exception was thrown trying to copy
file"); Console.WriteLine();
return;
}
Console.WriteLine("...Done");
}
}
}
}

```

- Chương trình thực hiện bằng cách sau khi biên dịch ra tập tin filecopy.exe ta gọi thực hiện tập tin này với tham số dòng lệnh như sau: filecopy.exe filecopy.cs filecopy.bak
- Tập tin filecopy.cs đã hiện hữu và tập tin filecopy.bak thì chưa hiện hữu cho đến khi lệnh này thực thi. Sao khi thực thi xong chương trình tập tin filecopy.bak được tạo ra. Nếu chúng ta thực hiện chương trình lần thứ hai cũng với các tham số như vậy, thì chúng ta sẽ nhận được kết quả xuất như sau: Copy...
- filecopy.bak already exists!
  Nếu chúng ta thực hiện chương trình mà không có bất cứ tham số nào, hay chỉ có một tham số, chúng ta sẽ nhận được kết quả như sau : Format d:\working\filecopy\filecopy.exe orig-file new-file
  Cuối cùng, điều tệ nhất xảy ra là chúng ta thực hiện sao chép nhưng tập tin nguồn không tồn tại: Copy...
- filecopy.cs does not exist!
- Như chúng ta ta thấy tất cả các kết quả có thể có của chương trình minh họa 12.5 trên.
  Chương trình thực hiện việc sao chép một tập tin và nó kiểm tra tất cả các tình huống có thể có và thực hiện việc xử lý các ngoại lệ. Điều này cho thấy chương trình vừa đáp ứng được mặt logic của lập trình vừa đáp ứng được việc xử lý các ngoại lệ.
  Như chúng ta biết trong lệnh sau:
- string[] CLA = Environment.GetCommandLineArgs(); thực hiện việc lấy các tham số dòng lệnh được cấp cho chương trình. Lớp Environment này chúng ta đã tìm hiểu và đã sử dụng trong phần trước.
  Lệnh sau kiểm tra xem chương trình có nhận được ít hởn giá trị tham số dòng lệnh hay không.

```c#
if ( CLA.Length < 3)
{
    Console.WriteLine("Format: {0} orig-file new-file", CLA[0]);
}
```

- Nếu giá trị này nhỏ hơn 3, người sử dụng đã không cung cấp đủ thông tin. Nên nhớ rằng,
  sử dụng phương thức GetCommandLineArgs, thì giá trị đầu tiên mà chúng ta nhận được
  là tên của chương trình.
- Phần còn lại là các tham số dòng lệnh được theo sau. Điều này có nghĩa rằng chúng ta cần thiết 3 giá trị: tên chương trình, tên tập tin nguồn, tên tập tin mới. Nếu chúng ta nhập vào không đủ 3 tham số dòng lệnh, thì chương trình sẽ xuất ra thông báo với tên của chương trình thực hiện được đọc bởi GetCommandLineArgs.
- Nếu cung cấp đầy đủ các tham số, việc xử lý sao chép sẽ được thực hiện. Để dễ theo dõi thì chương trình xuất ra thông báo việc sao chép file:

```
Console.Write("Copy...");
..... Console.WriteLine("...Done");
```

- Mặc dùng việc sao chép tập tin không có gì phức tạp, nhưng chúng ta lưu ý rằng trong chương trình trên chúng ta có thêm vào các đoạn xử lý ngoại lệ. Việc gọi hàm Copy của File được bao bọc trong khối try, và sau đó là ba thể hiện của Catch theo sau. Bởi vì có rất nhiều thứ có thể gây ra lỗi do các hoạt động trên tập tin, đề nghị rằng chúng ta nên đảm bảo cho chương trình của chúng ta thực hiện việc bắt giữ và xử lý các ngoại lệ
  tương ứng.
- Hầu hết những phương thức File có những ngoại lệ đã được định nghĩa cho một số các lỗi quan trọng có thể xuất hiện. Khi chúng ta tra cứu tài liệu trực tuyến cho một lớp.
- Chúng ta sẽ tìm thấy bất cứ những ngoại lệ nào được định nghĩa cho phương thức đưa ra. Một cách thực hành lập trình tốt là thêm vào các đoạn xử lý ngoại lệ với bất cứ ngoại lệ nào có thể xuất hiện. Trong chương trình ngoại lệ đầu tiên được xử lý cho việc gọi hàm Copy() là:

```c#
catch (System.IO.FileNotFoundException)
{
Console.WriteLine("\n{0} does not exist!", origfile);
return;
}
```

- Ngoại lệ này được phát sinh khi một tập tin mà chúng ta cố sao chép không tìm thấy, ngoại lệ này được đặt tên là FileNotFoundException.

- Ngoại lệ tiếp theo được bắt là IOException. Ngoại lệ này được phát sinh từ một số ngoại lệ khác. Bao gồm một thư mục không tìm thấy (DirectoryNotFoundException), kết thúc của tập tin không đựơc tìm thấy (EndOfStreamException), có lỗi đọc tập tin (FileLoadException), hay là lỗi tập tin không được tìm thấy, nhưng ngoại lệ này sẽ được bắt trong xử lý ngoại lệ bên trên. Ngoại lệ này cũng được phát sinh khi tập tin mà chúng ta cần tạo mới đã tồn tại.
- Cuối cùng, chúng ta sẽ bắt giữ những ngoại lệ không mong đợi còn lại bằng sử dụng ngoại lệ chung hay ngoại lệ tổng quát. Bởi vì chúng ta không biết nguyên nhân của việc xảy ra ngoại lệ, ở đây chỉ có thể hiển thị thông điệp của chính bản thân ngoại lệ phát sinh.
- Nên sử dụng xử lý ngoại lệ khi thao tác trên tập tin. Phong cách lập trình tốt là không nên nghĩ rằng người sử dụng sẽ cung cấp cho chương trình mọi thứ mà chương trình cần nhất là khi sử dụng tham số dòng lệnh. Lấy thông tin về tập tin
- Ngoài lớp File được cung cấp từ thư viện cơ sở, một lớp khác cũng thường xuyên được sử dụng thể làm việc với tập tin là lớp FileInfo. Chương trình 12.6 minh họa việc sử dụng lớp này. Trong chương trình này sẽ lấy một tên tập tin và hiển thị kích thước và những ngày quan trọng liên quan đến việc tạo, bổ sung tập tin. Sử dụng lớp FileInfo.

```c# // Filsize.cs
namespace Programming_CSharp
{
using System; using System.IO;
public class Tester
{
public static void Main()
{
string[] CLA = Environment.GetCommandLineArgs();
FileInfo fiExe = new FileInfo( CLA[0] );
if ( CLA.Length < 2)
{
Console.WriteLine("Format: {0} filename", fiExe.Name);
}
else
{
try
{
FileInfo fiFile = new FileInfo( CLA[1]);
if (fiFile.Exists)
{
Console.WriteLine("******************************");
Console.WriteLine("{0}{1}",fiFile.Name, fiFile.Length);
Console.WriteLine("******************************");
Console.WriteLine("Last access:{0}",fiFile.LastAccessTime);
Console.WriteLine("Last write: {0}",
fiFile.LastWriteTime); Console.WriteLine("Creation: {0}",
fiFile.CreationTime);
Console.WriteLine("******************************");
}
else
{
Console.WriteLine("{0} doesn’t exist!", fiFile.Name);
}
}
catch (System.IO.FileNotFoundException)
{
Console.WriteLine("\n{0} does not exists!", CLA[1]);
return;
}
catch (Exception e)
{
Console.WriteLine("\n An exception was thrown trying to copy file"); Console.WriteLine();
return;
}// end catch
}// end else
}// end Main
}// end class
}// end namespace
```

```console
Kết quả:
******************************
filesize.cs 1360
******************************
Last access: 12/5/2002 12:00:00 AM
Last write:12/5/2002 5:50:50 PM
Creation: 12/5/2002 5:53:31 PM
******************************
```

- Một đối tượng FileInfo được tạo ra và gắn với một tập tin tương ứng:
- FileInfo fiInfo = new FileInfo( CLA[1]);
- Tham số của bộ khởi dựng lớp FileInfo xác định tên của tập tin mà nó sẽ chứa nhận thông tin, trong trường hợp này nó sẽ lấy tham số thứ hai của tham số dòng lệnh làm tập tin mà nó sẽ thực hiện. Nếu người dùng không nhập tên tập tin thì chương trình sẽ in ra tên của chương trình.
