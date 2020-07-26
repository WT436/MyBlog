Nạp chồng phương thức

Một ký hiệu (signature) của một phương thức được định nghĩa như tên của phương thức
cùng với danh sách tham số của phương thức. Hai phương thức khác nhau khi ký hiệu
của chúng khác là khác nhau tức là khác nhau khi tên phương thức khác nhau hay danh
sách tham số khác nhau. Danh sách tham số được xem là khác nhau bởi số lượng các
tham số hoặc là kiểu dữ liệu của tham số. Ví dụ đoạn mã sau, phương thức thứ nhất khác
phương thức thứ hai do số lượng tham số khác nhau. Phương thức thứ hai khác phương
thức thứ ba do kiểu dữ liệu tham số khác nhau:

void myMethod( int p1 );
void myMethod( int p1, int p2 );
void myMethod( int p1, string p2 );

Một lớp có thể có bất cứ số lượng phương thức nào, nhưng mỗi phương thức trong lớp
phải có ký hiệu khác với tất cả các phương thức thành viên còn lại của lớp.

Ví dụ sau minh họa lớp Time có hai phương thức khởi dựng, một phương thức nhận
tham số là một đối tượng DateTime còn phương thức thứ hai thì nhận sáu tham số
nguyên.

Minh họa nạp chồng phương thức khởi dựng.

-----------------------------------------------------------------------------

using System;
public class Time
{
public void DisplayCurrentTime()
{
Console.WriteLine("{0}/{1}/{2} {3}:{4}:{5}", Date, Month,
Year, Hour, Minute, Second);
}
public Time( System.DateTime dt)
{
Year = dt.Year;
Month = dt.Month;
Date = dt.Day;
Hour = dt.Hour;
Minute = dt.Minute;
Second = dt.Second;
}
public Time(int Year, int Month, int Date, int Hour, int
Minute, int Second)
{
this.Year = Year;
this.Month = Month;
this.Date = Date;
this.Hour = Hour;
this.Minute = Minute;
this.Second = Second;
}
private int Month;
private int Date;
private int Hour;

private int Minute;
private int Second;
}
public class Tester
{
static void Main()
{
System.DateTime currentTime = System.DateTime.Now;
Time t1 = new Time( currentTime);
t1.DisplayCurrentTime();
Time t2 = new Time(2002,6,8,18,15,20);
t2.DisplayCurrentTime();
}
}

-----------------------------------------------------------------------------

Kết quả:
2/1/2002 17:50:17
8/6/2002 18:15:20

-----------------------------------------------------------------------------

Như chúng ta thấy, lớp Time trong ví dụ minh họa 4.9 có hai phương thức khởi dựng.
Nếu hai phương thức có cùng ký hiệu thì trình biên dịch sẽ không thể biết được gọi
phương thức nào khi khởi tạo hai đối tượng là t1 và t2. Tuy nhiên, ký hiệu của hai
phương thức này khác nhau vì tham số truyền vào khác nhau, do đó trình biên dịch sẽ
xác định được phương thức nào được gọi dựa vào các tham số.

Khi thực hiện nạp chồng một phương thức, bắt buộc chúng ta phải thay đổi ký hiệu của
phương thức, số tham số, hay kiểu dữ liệu của tham số. Chúng ta cũng có thể toàn quyền
thay đổi giá trị trả về, nhưng đây là tùy chọn. Nếu chỉ thay đổi giá trị trả về thì không
phải nạp chồng phương thức mà khi đó hai phương thức khác nhau, và nếu tạo ra hai
phương thức cùng ký hiệu nhưng khác nhau kiểu giá trị trả về sẽ tạo ra một lỗi biên dịch.

Nạp chồng phương thức.

-----------------------------------------------------------------------------

using System;
public class Tester
{
private int Triple( int val)
{
return 3*val;
}
private long Triple(long val)
{
return 3*val;
}
public void Test()
{
int x = 5;
int y = Triple(x);
Console.WriteLine("x: {0} y: {1}", x, y);
long lx = 10;
long ly = Triple(lx);
Console.WriteLine("lx: {0} ly:{1}", lx, ly);
}
static void Main()
{
Tester t = new Tester();
t.Test();
}
}

-----------------------------------------------------------------------------

Kết quả: x: 5 y: 15 lx: 10 ly:30

-----------------------------------------------------------------------------

Trong ví dụ này, lớp Tester nạp chồng hai phương thức Triple(), một phương thức nhận
tham số nguyên int, phương thức còn lại nhận tham số là số nguyên long. Kiểu giá trị trả
về của hai phương thức khác nhau, mặc dù điều này không đòi hỏi nhưng rất thích hợp
trong trường hợp này.
