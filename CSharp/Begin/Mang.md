# Mảng

- Ngôn ngữ C# cung cấp cú pháp chuẩn cho việc khai báo những đối tượng Array. Tuy nhiên, cái thật sự được tạo ra là đối tượng của kiểu System.Array. Mảng trong ngôn ngữ C# kết hợp cú pháp khai báo mảng theo kiểu ngôn ngữ C và kết hợp với định nghĩa lớp do đó thể hiện của mảng có thể truy cập những phương thức và thuộc tính của System.Array.

Một số các thuộc tính và phương thức của lớp System.Array

- BinarySearch() : Phương thức tĩnh public tìm kiếm một mảng một chiều đã sắp thứ tự
- Clear() : Phương thức tĩnh public thiết lập các thành phần của mảng về 0 hay null.
- Copy() : Phương thức tĩnh public đã nạp chồng thực hiện sao chép một vùng của mảng vào mảng khác.
- CreateInstance() : Phương thức tĩnh public đã nạp chồng tạo một thể hiện mới cho mảng
- IndexOf() : Phương thức tĩnh public trả về chỉ mục của thể hiện đầu tiên chứa giá trị trong mảng một chiều
- LastIndexOf() : Phương thức tĩnh public trả về chỉ mục của thể hiện cuối cùng của giá trị trong mảng một chiều
- Reverse() : Phương thức tĩnh public đảo thứ tự của các thành phần trong mảng một chiều
- Sort() : Phương thức tĩnh public sắp xếp giá trị trong mảng một chiều.
- IsFixedSize : Thuộc tính public giá trị bool thể hiện mảng có kích thước cố định hay không.
- IsReadOnly : Thuộc tính public giá trị bool thể hiện mảng chỉ đọc hay không
- IsSynchronized : Thuộc tính public giá trị bool thể hiện mảng có hỗ trợ thread-safe
- Length : Thuộc tính public chiều dài của mảng
- Rank : Thuộc tính public chứa số chiều của mảng
- SyncRoot Thuộc tính public chứa đối tượng dùng để đồng bộ truy cập trong mảng
- GetEnumerator() Phương thức public trả về IEnumerator
- GetLength() Phương thức public trả về kích thước của một chiều cố định trong mảng
- GetLowerBound() Phương thức public trả về cận dưới của chiều xác định trong mảng
- GetUpperBound() Phương thức public trả về cận trên của chiều xác định trongmảng
- Initialize() Khởi tạo tất cả giá trị trong mảng kiểu giá trị bằng cách gọi bộ khởi dụng mặc định của từng giá trị.
- SetValue() Phương thức public thiết lập giá trị cho một thành phần xácđịnh trong mảng.

### Khai báo mảng

Chúng ta có thể khai báo một mảng trong C# với cú pháp theo sau: < kiểu dữ liệu > [] < tên mảng >
Ta có khai báo như sau: int[] myIntArray;
Cặp dấu ngoặc vuông ([]) báo cho trình biên dịch biết rằng chúng ta đang khai báo một mảng. Kiểu dữ liệu là kiểu của các thành phần chứa bên trong mảng. Trong ví dụ bên trên. myIntArray được khai báo là mảng số nguyên.
Chúng ta tạo thể hiện của mảng bằng cách sử dụng từ khóa new như sau: myIntArray = new int[6];
Khai báo này sẽ thiết lập bên trong bộ nhớ một mảng chứa sáu số nguyên. Dành cho lập trình viên Visual Basic, thành phần đầu tiên luôn bắt đầu 0, không có cách nào thiết lập cận trên và cận dưới của mảng, và chúng ta cũng không thể thiết lập lại kích thước của mảng.
Điều quan trọng để phân biệt giữa bản thân mảng (tập hợp các thành phần) và các thành phần trong mảng. Đối tượng myIntArray là một mảng, thành phần là năm số nguyên được lưu giữ. Mảng trong ngôn ngữ C# là kiểu dữ liệu tham chiếu, được tạo ra trên heap.
Do đó myIntArray được cấp trên heap. Những thành phần của mảng được cấp phát dựa trên các kiểu dữ liệu của chúng. Số nguyên là kiểu dữ liệu giá trị, và do đó những thành phần của myIntArray là kiểu dữ liệu giá trị, không phải số nguyên được boxing. Một mảng của kiểu dữ liệu tham chiếu sẽ không chứa gì cả nhưng tham chiếu đến những thành phần được tạo ra trên heap

#### Giá trị mặc định

Khi chúng ta tạo một mảng có kiểu dữ liệu giá trị, mỗi thành phần sẽ chứa giá trị mặc định của kiểu dữ liệu (xem danh sách trên, kiểu dữ liệu và các giá trị mặc định). Với khai báo: myIntArray = new int[5]; sẽ tạo ra một mảng năm số nguyên, và mỗi thành phần được thiết lập giá trị mặc định là 0, đây cũng là giá trị mặc định của số nguyên.
Không giống với mảng kiểu dữ liệu giá trị, những kiểu tham chiếu trong một mảng không được khởi tạo giá trị mặc định. Thay vào đó, chúng sẽ được khởi tạo giá trị null. Nếu chúng ta cố truy cập đến một thành phần trong mảng kiểu dữ liệu tham chiếu trước khi chúng được khởi tạo giá trị xác định, chúng ta sẽ tạo ra một ngoại lệ.
Giả sử chúng ta tạo ra một lớp Button. Chúng ta khai báo một mảng các đối tượng Button với cú pháp sau:
Button[] myButtonArray; và chúng ta tạo thể hiện của mảng như sau: myButtonArray = new Button[3];
Chúng ta có thể viết ngắn gọn như sau: Button muButtonArray = new Button[3];
Không giống với ví dụ mảng số nguyên trước, câu lệnh này không tao ra một mảng với những tham chiếu đến ba đối tượng Button. Thay vào đó việc này sẽ tạo ra một mảng myButtonArray với ba tham chiếu null. Để sử dụng mảng này, đầu tiên chúng ta phải tạo và gán đối tượng Button cho từng thành phần tham chiếu trong mảng. Chúng ta có thể tạo đối tượng trong vòng lặp và sau đó gán từng đối tượng vào trong mảng.

#### Truy cập các thành phần trong mảng

Để truy cập vào thành phần trong mảng ta có thể sử dụng toán tử chỉ mục ([]). Mảng dùng cơ sở 0, do đó chỉ mục của thành phần đầu tiên trong mảng luôn luôn là 0. Như ví dụ trước thành phần đầu tiên là myArray[0]. Như đã trình bày ở phần trước, mảng là đối tượng, và do đó nó có những thuộc tính. Một trong những thuộc tính hay sử dụng là Length, thuộc tính này sẽ báo cho biết số đối tượng trong một mảng. Một mảng có thể được đánh chỉ mục từ 0 đến Length –1. Do đó nếu có năm thành phần trong mảng thì các chỉ mục là: 0, 1, 2, 3, 4.

#### Khởi tạo thành phần của mảng

Chúng ta có thể khởi tạo nội dung của một mảng ngay lúc tạo thể hiện của mảng bằng cách đặt những giá trị bên trong dấu ngoặc ({}). C# cung cấp hai cú pháp để khởi tạo các thành phần của mảng, một cú pháp dài và một cú pháp ngắn:
int[] myIntArray = new int[5] { 2, 4, 6, 8, 10};
int[] myIntArray = { 2, 4, 6, 8, 10};
Không có sự khác biệt giữa hai cú pháp trên, và hầu hết các chương trình đều sử dụng cú pháp ngắn hơn do sự tự nhiên và lười đánh nhiều lệnh của người lập trình.

#### Sử dụng từ khóa params

Chúng ta có thể tạo một phương thức rồi sau đó hiển thị các số nguyên ra màn hình console bằng cách truyền vào một mảng các số nguyên và sử dụng vòng lặp foreach để duyệt qua từng thành phần trong mảng. Từ khóa params cho phép chúng ta truyền một số biến của tham số mà không cần thiết phải tạo một mảng.
Trong ví dụ kế tiếp, chúng ta sẽ tạo một phương thức tên DisplayVals(), phương thức này sẽ lấy một số các biến của tham số nguyên: public void DisplayVals( params int[] intVals) Phương thức có thể xem mảng này như thể một mảng được tạo ra tường minh và được truyền vào tham số. Sau đó chúng ta có thể tự do lặp lần lượt qua các thành phần trong mảng giống như thực hiện với bất cứ mảng nguyên nào khác

#### Câu lệnh lặp foreach

Câu lệnh lặp foreach khá mới với những người đã học ngôn ngữ C, từ khóa này được sử dụng trong ngôn ngữ Visual Basic. Câu lệnh foreach cho phép chúng ta lặp qua tất cả các mục trong một mảng hay trong một tập hợp.
Cú pháp sử dụng lệnh lặp foreach như sau:
foreach ( < kiểu dữ liệu thành phần > < tên truy cập > in < mảng/tập hợp > ) {
// thực hiện thông qua < tên truy cập > tương ứng với từng mục trong mảng hay tập hợp
}
Do vậy, chúng ta có thể cải tiến ví dụ trước bằng cách thay việc sử dụng vòng lặp for bằng vòng lặp foreach để truy cập đến từng thành phần trong mảng. Sử dụng foreach

```c#
namespace Programming_CSharp
{
    using System; // tạo một lớp đơn giản để lưu trữ trong mảng
    public class Employee
    {
        // biến thành viên
        private private int empID;
        private int size;
        // bộ khởi tạo lấy một tham số
        public Employee( int empID )
        {
            this.empID = empID;
        }
        public override string ToString()
        {
            return empID.ToString();
        }
    }
    public class Tester {
        static void Main()
        {
            int[] intArray;
            Employee[] empArray;
            intArray = new int[5];
            empArray = new Employee[3]; // tạo đối tượng đưa vào mảng
            for( int i = 0;i < empArray.Length; i++)
            {
                empArray[i] = new Employee(i+10);
            } // xuất mảng nguyên
            foreach (int i in intArray)
            {
                Console.Write(i.ToString()+"\t");
            } // xuất mảng Employee
            foreach ( Employee e in empArray)
            {
                Console.WriteLine(e.ToString()+"\t");
            }
        }
    }
}
```

Kết quả của ví dụ trên. Tuy nhiên, với việc sử dụng vòng lặp for ta phải xác định kích thước của mảng, sử dụng biến đếm tạm thời để truy cập đến từng thành phần trong mảng:
