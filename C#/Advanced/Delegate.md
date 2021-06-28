# Delegate

Đầu tiên chúng ta cần hiểu rõ con trot hàm nó là cái gì?

Con trỏ hàm là một biến lưu trữ địa chỉ của một hàm, thông qua biến đó, có thể gọi hàm mà nó trỏ tới. Điều này rất thuận tiện khi muốn định nghĩa các chức năng khác nhau cho một nhóm các đối tượng khá giống nhau.

## Vậy nó có liên quan gì đến Delegate?

Nam viết lib rồi đúng không? biết Func đúng không? Khi xây dựng một class để dùng một việc gì đó. Nếu như class đó được sinh ra trong một mục đích đã xác định và chỉ có tác dụng gộp code , làm ngắn code thì chúng ta không bàn đến ở đây. Điều mà chúng ta đau đầu nhất là Tính toán kiểu gì? và truyền dạng nào vào?. có khi chỉ 1 class, có khi 1 hàm, có khi lại là một biểu thức logic, có khi lại là 1 labda..... Oh trời đất ơi! Mi đùa ta đấy hả. Không! Nó chỉ là dạng kiểu dữ liệu đặc biệt thôi! Những lúc khoai lang tím như vậy Delegate được khai sinh. Giống thằng cha todicodedao nói :"Nó khiến java thèm ..... ak mà thôi!".

Ví dụ khác . nếu ai làm Winform, WPF or LINQ rồi thì chắc sẽ từng gặp những quả load form do chờ sử lý sự kiện. Hay chờ dữ liệu trả về. 

Delegate là kiểu dữ liệu trong c# mà biến tạo ra từ nó chứa tham chiếu tới phương thức, thay vì chứa giá trị hoặc chứa tham chiếu tới object của các class bình thường.

## Vai trò của Delegate Là gì?

- Giúp class uyển chuyển , linh động hơn trong việc sử dụng Method.
- Phân chia logic của class ra làm các phần khác nhau.
- Giúp class Object tương tác ngược trở lại với entity.
- Cốt lõi của lập trình hướng sự kiện.
- Song hành cùng với lập trình bất đồng bộ dạng Callback hoặc trong  Multi-threading

## Khai Báo

- Khai báo ở cấp độ class

```c#
public delegate int MyDelegate (string s);
//Syntax 
delegate <return type> <delegate-name> <parameter list>
```

- Sau khi khi báo kiểu, có thể khai báo biến thuộc kiểu dữ liệu này tương tự như khai báo các biến bình thường khác: 

```c#
/* khai báo property thuộc kiểu MyDelegate.
 * MyDelegate được sử dụng như những kiểu dữ liệu thông thường
 */
public MyDelegate Function { get; set; }
```

Và hiển nhiên nó cx sẽ được gán như bình thường.

```c#
/* phương thức này có 1 tham số đầu vào là kiểu delegate MyDelegate.
 * Kiểu delegate làm tham số không khác gì kiểu dữ liệu bình thường
 */        
public void Render(MyDelegate function, double[] range)
{
    // có thể gán biến thuộc kiểu delegate như bình thường
    Function = function;
}
```

- Biến của delegate cũng chỉ là một dạng của object. Nó cũng có thuộc tính và phương thức.
- Do biến delegate chưa tham chiếu đến một phương thức. Nên ta sẽ sử dụng biến delegate như một phương thức thông thường.

Ngoài ra : biến delegate còn có một kiểu giúp nó gọi phuong thức mà biến này đang trỏ tới đó là Invoke();

## Truyền tham số kiểu delegate cho Method

Giai đoạn này thực chất là lúc chúng ta sử dụng class và truyền kiểu delegate vào cho Method.

## Generic delegate

Cái này khá hay vì khởi tạo,sử dụng ... nó lằng nhằng quá!

Các kiểu định sẵn bao gồm 3 loại : Actions,Funcs,Predicates.

1. Actions

là kiểu  delegate tương ứng với các kiểu dữ liệu không trả về

```c#
namespace System
{
    public delegate void Action();
    public delegate void Action<in T>(T obj);
    public delegate void Action<in T1, in T2>(T1 arg1, T2 arg2);
    // còn các delegate tương tự như vậy nữa
    // .NET framework định nghĩa tổng cộng 16 delegate như vậy với số lượng tham số đầu vào từ 1 đến 16.
}
```

2. Funcs

Các phương thức có trả về dữ liệu:

```c#
namespace System
{
    public delegate TResult Func<out TResult>();
    public delegate TResult Func<in T, out TResult>(T arg);
    public delegate TResult Func<in T1, in T2, out TResult>(T1 arg1, T2 arg2);
    // có 17 delegate tương tự như vậy
}
```

3. Predicates

Là kiểu Delegate được định nghĩa sẵn :

```c#
namespace System
{    
    public delegate bool Predicate<[NullableAttribute(2)] in T>(T obj);
}
```

Ngoài ra cách dừng với delegate còn có : phương thức vô danh , labda, hàm cục bộ .....
Trong khi cách khai báo , cách dùng có 3 loại. kết hợp generic cũng có tương tự với từng loại.
.....

Trên đây chỉ khái quát bộ khung chính cho delegate. còn cách dùng , thủ thuật .... sẽ không có ở đây.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>