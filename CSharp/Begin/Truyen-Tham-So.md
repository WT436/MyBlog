# Truyền tham số

- Ngôn ngữ C# đưa ra một bổ sung tham số là ref cho phép truyền các đối tượng giá trị vào trong phương thức theo kiểu tham chiếu. Và tham số bổ sung out trong trường hợp muốn truyền dưới dạng tham chiếu mà không cần phải khởi tạo giá trị ban đầu cho tham số truyền. Ngoài ra ngôn ngữ C# còn hỗ trợ bổ sung params cho phép phương thức chấp nhận nhiều số lượng các tham số.

1. Truyền tham chiếu

- Những phương thức chỉ có thể trả về duy nhất một giá trị, mặc dù giá trị này có thể là một tập hợp các giá trị. Nếu chúng ta muốn phương thức trả về nhiều hơn một giá trị thì cách thực hiện là tạo các tham số dưới hình thức tham chiếu. Khi đó trong phương thức ta sẽ xử lý và gán các giá trị mới cho các tham số tham chiếu này, kết quả là sau khi phương thức thực hiện xong ta dùng các tham số truyền vào như là các kết quả trả về.
  Ví dụ sau minh họa việc truyền tham số tham chiếu cho phương thức.

```c#
using System;
 public class Time {
    private int Year;
    private int Month;
    private int Date;
    private int Hour;
    private int Minute;
    private int Second;
    public void  DisplayCurrentTime()
    {
        Console.WriteLine("{0}/{1}/{2}/{3}:{4}:{5}", Date, Month, Year, Hour, Minute, Second);
    }
    public int GetHour()
    {
        return Hour;
    }
    public void GetTime(int h, int m, int s)
    {
      h = Hour;
      m = Minute;
      s = Second;
    }
     public Time( System.DateTime dt) {
         Year = dt.Year;
         Month = dt.Month;
         Date = dt.Day;
         Hour = dt.Hour;
         Minute = dt.Minute;
         Second = dt.Second;
    }
}
public class Tester
{
    static void Main()
    {
        System.DateTime currentTime= System.DateTime.Now;
        Time t = new Time( currentTime);
        t.DisplayCurrentTime();
        int theHour = 0; int theMinute  = 0;
        int theSecond = 0;
        t.GetTime( theHour, theMinute,theSecond);
        System.Console.WriteLine("Current time:{0}:{1}:{2}",theHour, theMinute, theSecond);
    }
}
```

- Như ta thấy, kết quả xuất ra ở dòng cuối cùng là ba giá trị 0:0:0, rõ ràng phương thức GetTime() không thực hiện như mong muốn là gán giá trị Hour, Minute, Second cho các tham số truyền vào. Tức là ba tham số này được truyền vào dưới dạng giá trị. Do đó để thực hiện như mục đích của chúng ta là lấy các giá trị của Hour, Minute, Second thì phương thức GetTime() có ba tham số được truyền dưới dạng tham chiếu. Ta thực hiện như sau, đầu tiên, thêm là thêm khai báo ref vào trước các tham số trong phương thức
  GetTime():

```c#
public void GetTime( ref int h, ref int m, ref int s)
{
    h= Hour;
    m = Minute;
    s = Second;
}
```

2. Truyền tham chiếu với biến chưa khởi tạo

- Ngôn ngữ C# bắt buộc phải thực hiện một phép gán cho biến trước khi sử dụng, do đó khi khai báo một biến như kiểu cơ bản thì trước khi có lệnh nào sử dụng các biến này thì phải có lệnh thực hiện việc gán giá trị xác định cho biến. Như trong ví dụ trên, nếu chúng ta không khởi tạo biến theHour, theMinute, và biến theSecond trước khi truyềnnhư tham số vào phương thức GetTime() thì trình biên dịch sẽ báo lỗi. Nếu chúng ta sửa lại đoạn mã của ví dụ trước như sau:

```c#
int theHour;
int theMinute;
int theSecond;
t.GetTime( ref int theHour, ref int theMinute, ref int theSecond);

```

- biên dịch với đoạn mã lệnh như trên sẽ được báo các lỗi sau:
  Use of unassigned local variable ‘theHour’
  Use of unassigned local variable ‘theMinute’
  Use of unassigned local variable ‘theSecond’

- Để mở rộng cho yêu cầu trong trường hợp này ngôn ngữ C# cung cấp thêm một bổ sung tham chiếu là out. Khi sử dụng tham chiếu out thì yêu cầu bắt buộc phải khởi tạo các tham số tham chiếu được bỏ qua. Như các tham số trong phương thức GetTime(), các tham số này không cung cấp bất cứ thông tin nào cho phương thức mà chỉ đơn giản là cơ chế nhận thông tin và đưa ra bên ngoài. Do vậy ta có thể đánh dấu tất cả các tham số tham chiếu này là out, khi đó ta sẽ giảm được công việc phải khởi tạo các biến này trước khi đưa vào phương thức. Lưu ý là bên trong phương thức có các tham số tham chiếu out thì các tham số này phải được gán giá trị trước khi trả về. Ta có một số thay đổi cho phương thức GetTime() như sau:

```c#
public void GetTime( out int h, out int m, out int s)
{
    h = Hour;
    m = Minute;
    s = Second;
}
```

và cách gọi mới phương thức GetTime() trong Main():

```c#
t.GetTime( out theHour, out theMinute, out theSecond);
```
