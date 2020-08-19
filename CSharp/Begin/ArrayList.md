# ArrayList

Việc sử dụng mảng có kích thước cố định là không thích hợp cũng như là chúng ta không thể đoán trước được kích thước của mảng cần thiết.
Lớp ArrayList là một kiểu dữ liệu mảng mà kích thước của nó được gia tăng một cách động theo yêu cầu. ArrayList cung cấp một số phương thức và những thuộc tính cho những thao tác liên quan đến mảng. Một vài phương thức và thuộc tính quan trọng của ArrayList được liệt kê như sau:

- Adapter() Phương thức static tạo một wrapper ArrayList cho đốitượng IList
- FixedSize() Phương thức static nạp chồng trả về sanh sách đối tượng như là một wrapper. Danh sách có kích thước cố định, các thành phần của nó có thể được sửa chữa nhưng không thểthêm hay xóa.
- ReadOnly() Phương thức static nạp chồng trả về danh sách lớp như là một wrapper, chỉ cho phép đọc.
- Repeat() Phương thức static trả về một ArrayList mà những thànhphần của nó được sao chép với giá trị xác định.
- Synchronized() Phương thức static trả về danh sách wrapper được thread-safe
- Capacity Thuộc tính để get hay set số thành phần trong ArrayList.
- Count Thuộc tính nhận số thành phần hiện thời trong mảng
- IsFixedSize Thuộc tính kiểm tra xem kích thước của ArrayList có cốđịnh hay không
- IsReadOnly Thuộc tính kiểm tra xem ArrayList có thuộc tính chỉ đọc hay không.
- IsSynchronized Thuộc tính kiểm tra xem ArrayList có thread-safe haykhông
- Item() Thiết lập hay truy cập thành phần trong mảng tại vị trí xácđịnh. Đây là bộ chỉ mục cho lớp ArrayList.
- SyncRoot Thuộc tính trả về đối tượng có thể được sử dụng để đồngbộ truy cập đến ArrayList
- Add() Phương thức public để thêm một đối tượng vào ArrayList
- AddRange() Phương thức public để thêm nhiều thành phần của mộtICollection vào cuối của ArrayList
- BinarySearch() Phương thức nạp chồng public sử dụng tìm kiếm nhị phận để định vị một thành phần xác định trong ArrayList được sắp xếp.
- Clear() Xóa tất cả các thành phần từ ArrayList
- Clone() Tạo một bản copy
- Contains() Kiểm tra một thành phần xem có chứa trong mảng haykhông
- CopyTo() Phương thức public nạp chồng để sao chép một ArrayListđến một mảng một chiều.
- GetEnumerator() Phương thức public nạp chồng trả về một enumerator dùngđể lặp qua mảng
- GetRange() Sao chép một dãy các thành phần đến một ArrayList mới
- IndexOf() Phương thức public nạp chồng trả về chỉ mục vị trí đầu tiênxuất hiện giá trị
- Insert() Chèn một thành phần vào trong ArrayList
- InsertRange(0 Chèn một dãy tập hợp vào trong ArrayList
- LastIndexOf() Phương thức public nạp chồng trả về chỉ mục trị trí cuối cùng xuất hiện giá trị.
- Remove() Xóa sự xuất hiện đầu tiên của một đối tượng xác định.
- RemoveAt() Xóa một thành phần ở vị trí xác định.
- RemoveRange() Xóa một dãy các thành phần.
- Reverse() Đảo thứ tự các thành phần trong mảng.
- SetRange() Sao chép những thành phần của tập hợp qua dãy nhữngthành phần trong ArrayList.
- Sort() Sắp xếp ArrayList.
- ToArray() Sao chép những thành phần của ArrayList đến một mảngmới.
- TrimToSize() Thiết lập kích thước thật sự chứa các thành phần trongArrayList

Khi tạo đối tượng ArrayList, không cần thiết phải định nghĩa số đối tượng mà nó sẽ chứa. Chúng ta thêm vào ArrayList bằng cách dùng phương thức Add(), và danh sách sẽ quan lý những đối tượng bên trong mà nó lưu giữ.
Với lớp Array phải định nghĩa số đối tượng mà mảng sẽ lưu giữ. Nếu cố thêm các thành phần vào trong mảng vượt quá kích thước mảng thì lớp mảng sẽ phát sinh ra ngoại lệ. Với ArrayList thì không cần phải khai báo số đối tượng mà nó lưu giữ.
