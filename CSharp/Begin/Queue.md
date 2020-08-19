# Hàng đợi (Queue)

Hàng đợi là kiểu dữ liệu tốt để quản lý những nguồn tài nguyên giới hạn. Ví dụ, chúng ta muốn gởi thông điệp đến một tài nguyên mà chỉ xử lý được duy nhất một thông điệp một lần. Khi đó chúng ta sẽ thiết lập một hàng đợi thông điệp để xử lý các thông điệp theo thứ tự đưa vào. Lớp Queue thể hiện kiểu dữ liệu như trên, trong sau liệt kê những phương thức và thuộc tính thành viên

- Synchronized() : Phương thức static trả về một Queue wrapper đượcthread-safe.
- Count : Thuộc tính trả về số thành phần trong hàng đợi
- IsReadOnly : Thuộc tính xác định hàng đợi là chỉ đọc
- IsSynchronized : Thuộc tính xác định hàng đợi được đồng bộ
- SyncRoot : Thuộc tính trả về đối tượng có thể được sử dụng để đồng bộ truy cập Queue.
- Clear() : Xóa tất cả các thành phần trong hàng đợi
- Clone() : Tạo ra một bản sao
- Contains() : : Xác định xem một thành phần có trong mảng.
- CopyTo() : Sao chép những thành phần của hàng đợi đến mảngmột chiều đã tồn tại
- Dequeue() : Xóa và trả về thành phần bắt đầu của hàng đợi.
- Enqueue() : Thêm một thành phần vào hàng đợi.
- GetEnumerator() : Trả về một enumerator cho hàng đợi.
- Peek() : Trả về phần tử đầu tiên của hàng đợi và không xóa nó.
- ToArray() : Sao chép những thành phần qua một mảng mới
  Chúng ta có thể thêm những thành phần vào trong hàng đợi với phương thức Enqueue và sau đó lấy chúng ra khỏi hàng đợi với Dequeue hay bằng sử dụng enumerator. Ví dụ sau minh họa việc sử dụng hàng đợi.

```c#
namespace Programming_CSharp
{
    using System;
    using System.Collections;
        public class Tester
        {
            public static void Main()
                {
            Queue intQueue = new Queue();
            // đưa vào trong mảng
            for(int i=0; i <5; i++)
            {
            intQueue.Enqueue(i*5);
            }
            // hiện thị hàng đợi
            Console.Write("intQueue values:\t");
            PrintValues( intQueue);
            // xóa thành phần ra khỏi hàng đợi
            Console.WriteLine("\nDequeue\t{0}", intQueue.Dequeue());
            // hiển thị hàng đợi
            Console.Write("intQueue values:\t");
            PrintValues(intQueue);
             // xóa thành phần khỏi hàng đợi
            Console.WriteLine("\nDequeue\t{0}", intQueue.Dequeue());
            // hiển thị hàng đợi
            Console.Write("intQueue values:\t");
            PrintValues(intQueue);
            // Xem thành phần đầu tiên trong hàng đợi.
            Console.WriteLine("\nPeek \t{0}", intQueue.Peek());
            // hiển thị hàng đợi
            Console.Write("intQueue values:\t");
            PrintValues(intQueue);
        }
        public static void PrintValues(IEnumerable myCollection)
        {
             IEnumerator myEnumerator = myCollection.GetEnumerator();
             while (myEnumerator.MoveNext()) Console.Write("{0} ",myEnumerator.Current);
            Console.WriteLine();
        }
    }
}
```

Trong ví dụ này ArrayList được thay bằng Queue, chúng ta cũng có thể Enqueue những đối tượng do ta định nghĩa. Trong trong chương trình trên đầu tiên ta đưa 5 số nguyên vào trong hàng đợi theo tứ tự 0 5 10 15 20. Sau khi đưa vào ta lấy ra phần tử đầu tiên là 0 nên hàng đợi còn lại 4 số là 5 10 15 20, lần thứ hai ta lấy ra 5 và chỉ còn 3 phần tử trong mảng 10 15 20. Cuối cùng ta dùng phương thức Peek() là chỉ xem phần tử đầu hàng đợi chứ không xóa chúng ra khỏi hàng đợi nên kết quả cuối cùng hàng đợi vẫn còn 3 số là 10 15 20. Một điểm lưu ý là lớp Queue là một lớp có thể đếm được enumerable nên ta có thể truyền vào phương thức PrintValues với kiểu tham số khai báo IEnumerable. Việc chuyển đổi này là ngầm định. Trong phương thức PrintValues ta gọi phương thức GetEnumerator, nên nhớ rằng đây là phương thức đơn của tất cả những lớp IEnumerable. Kết quả là một đối tượng Enumerator được trả về, do đó chúng ta có thể sử dụng chúng để liệt kê tất cả những đối tượng có trong tập hợp.
