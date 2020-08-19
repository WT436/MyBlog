Bảng chung

1.  IEnumerable Liệt kê thông qua một tập hợp bằng cách sử dụngforeach.
    Chúng ta có thể hỗ trợ cú pháp foreach trong lớp ListBoxTest bằng việc thực thi giao diện IEnumerator. Giao diện này chỉ có một phương thức duy nhất là GetEnumerator(), công việc của phương thức là trả về một sự thực thi đặc biệt của IEnumerator. Do vậy, ngữ nghĩa của lớp Enumerable là nó có thể cung cấp một Enumerator:

    ```c#
    public IEnumerator GetEnumerator()
    {
        return (IEnumerator) new ListBoxEnumerator(this);
    }
    ```

    - Enumerator phải thực thi những phương thức và thuộc tính IEnumerator. Chúng có thể được thực thi trực tiếp trong lớp chứa (trong trường hợp này là lớp ListBoxTest) hay bởi một lớp phân biệt khác. Cách tiếp cận thứ hai thường được sử dụng nhiều hơn, do chúng được đóng gói trong lớp Enumerator hơn là việc phân vào trong các lớp chứa.
    - Do lớp Enumerator được xác định cho lớp chứa, vì theo như trên thì lớp ListBoxEnumerator phải biết nhiều về lớp ListBoxTest. Nên chúng ta phải tạo cho nó một sự thực thi riêng chứa bên trong lớp ListBoxTest. Lưu ý rằng phương thức

    - GetEnumerator truyền đối tượng List- BoxTest hiện thời (this) cho enumerator. Điều này cho phép enumerator có thể liệt kê được các thành phần trong tập hợp của đối tượng ListBoxTest. Ở đây lớp thực thi Enumerator là ListBoxEnumerator, đây là một lớp private được định nghĩa bên trong lớp ListBoxTest. Lớp này thực thi đơn giản bao gồm một thuộc tính public, và hai phương thức public là MoveNext(), và Reset(). Đối tượng ListBoxTest được truyền vào như một đối mục của bộ khởi tạo. Ở đây nó được gán cho biến thành viên myLBT. Trong hàm khởi tạo này cũng thực hiện thiết lập giá trị biến thành viên index là -1, chỉ ra rằng chưa bắt đầu thực hiện việc enumerator đối tượng:

    ```c#
    public ListBoxEnumerator(ListBoxTest lbt)
    {
        this.lbt = lbt; index = -1;
    }
    ```

    - Phương thức MoveNext() gia tăng index và sau đó kiểm tra để đảm bảo rằng việc thực hiện không vượt quá số phần tử trong tập hợp của đối tượng:

    ```c#
    public bool MoveNext()
    {
        index++; if (index >=lbt.strings.Length)
        return false; else return true;
    }
    ```

    - Phương thức IEnumerator.Reset() không làm gì cả nhưng thiết lập lại giá trị của index là -1. Thuộc tính Current trả về đối tượng chuỗi hiện hành. Đó là tất cả những việc cần làm cho lớp ListBoxTest thực thi một giao diện IEnumerator. Câu lệnh foreach sẽ được gọi để đem về một enumerator, và sử dụng nó để liệt kê lần lượt qua các thành phần trong mảng.

- ICollection Thực thi bởi tất cả các tập hợp để cung cấp phương thức CopyTo() cũng như các thuộc tính Count - ISReadOnly, ISSynchronized, và SyncRoot.

  - Một giao diện quan trọng khác cho những mảng và cho tất cả những tập hợp được cung cấp bởi .NET Framework là ICollection. ICollection cung cấp bốn thuộc tính: Count, IsReadOnly, IsSynchronized, và SyncRoot. Ngoài ra ICollection cũng cung cấp một phương thức CopyTo(). Thuộc tính thường được sử dụng là Count, thuộc tính này trả về
    số thành phần trong tập hợp:
    for(int i = 0; i < myIntArray.Count; i++) { //... }
    Ở đây chúng ta sử dụng thuộc tính Count của myIntArray để xác định số đối tượng có thể được sử dụng trong mảng.

- IComparer So sánh giữa hai đối tượng lưu giữ trong tập hợp đểsắp xếp các đối tượng trong tập hợp.
  Giao diện IComparer cung cấp phương thức Compare(), để so sánh hai phần tử trong một tập hợp có thứ tự. Phương thức Compare() thường được thực thi bằng cách gọi phương thức CompareTo() của một trong những đối tượng.
  CompareTo() là phương thức có trong tất cả đối tượng thực thi IComparable. Nếu chúng ta muốn tạo ra những
  lớp có thể được sắp xếp bên trong một tập hợp thì chúng ta cần thiết phải thực thi IComparable. .NET Framework cung cấp một lớp Comparer thực thi IComparable và cung cấp một số thực thi cần thiết. Phần danh sách mảng sau sẽ đi vào chi tiết việc thực thi IComparable.

- IList Sử dụng bởi những tập hợp mảng được chỉ mục
- IDictionary Dùng trong các tập hợp dựa trên khóa và giá trị như Hashtable và SortedList.
- IDictionaryEnumerator Cho phép liệt kê dùng câu lệnh foreach qua tập hợphỗ trợ
- IDictionary.
