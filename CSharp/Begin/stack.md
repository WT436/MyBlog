# Ngăn xếp (stack)

- Ngăn xếp là một tập hợp mà thứ tự là vào trước ra sau hay vào sao ra trước (LIFO), tương như một chồng đĩa được xếp trong nhà hàng. Đĩa ở trên cùng tức là đĩa xếp sau thì được lấy ra trước do vậy đĩa nằm dưới đáy tức là đĩa đưa vào đầu tiên sẽ được lấy ra sau cùng.
- Hai phương thức chính cho việc thêm và xóa từ stack là Push và Pop, ngoài ra ngăn xếp cũng đưa ra phương thức Peek tương tự như Peek trong hàng đợi. Bảng sau minh họa các phương thức và thuộc tính của lớp Stack.

Synchronized() : Phương thức static trả về một Stack wrapperđược thread-safe.
Count : Thuộc tính trả về số thành phần trong ngăn xếp
IsReadOnly : Thuộc tính xác định ngăn xếp là chỉ đọc
IsSynchronized : Thuộc tính xác định ngăn xếp được đồng bộ
SyncRoot : Thuộc tính trả về đối tượng có thể được sử dụngđể đồng bộ truy cập Stack.
Clear() : Xóa tất cả các thành phần trong ngăn xếp
Clone() : Tạo ra một bản sao
Contains() : Xác định xem một thành phần có trong mảng.
CopyTo() : Sao chép những thành phần của ngăn xếp đếnmảng một chiều đã tồn tại
Pop() : Xóa và trả về phần tử đầu Stack
Push() : Đưa một đối tượng vào đầu ngăn xếp
GetEnumerator() : Trả về một enumerator cho ngăn xếp.
Peek() : Trả về phần tử đầu tiên của ngăn xếp và khôngxóa nó.
ToArray() : Sao chép những thành phần qua một mảng mới

- Ba lớp ArrayList, Queue, và Stack đều chứa phương thức nạp chồng CopyTo() và ToArray() dể sao chép những thành phần của chúng qua một mảng. Trong trường hợp của ngăn xếp phương thức CopyTo() sẽ chép những thành phần của chúng đến mảng một chiều đã hiện hữu, và viết chồng lên nội dung của mảng bắt đầu tại chỉ mục mà ta xác nhận. Phương thức ToArray() trả về một mảng mới với những nội dung của những thành phần trong mảng.
