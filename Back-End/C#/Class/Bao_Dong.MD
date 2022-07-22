Thuộc tính truy cập quyết định khả năng các phương thức của lớp bao gồm việc các
phương thức của lớp khác có thể nhìn thấy và sử dụng các biến thành viên hay những
phương thức bên trong lớp.  tóm tắt các thuộc tính truy cập của một lớp trong
C#.

public : Không hạn chế. Những thành viên được đánh dấupublic có thể được dùng
bởi bất kì các phương thức của lớp bao gồm những lớp khác.

private : Thành viên trong một lớp A được đánh dấu là privatethì chỉ được truy cập
bởi các phương thức của lớp A.  

protected : Thành viên trong lớp A được đánh dấu là protectedthì chỉ được các
phương thức bên trong lớp A và những phương thức dẫn xuất từ lớp A
truy cập.

internal : Thành viên trong lớp A được đánh dấu là internal thì được truy cập bởi
những phương thức của bất cứ lớpnào trong cùng khối hợp ngữ với A

protected internal  : Thành viên trong lớp A được đánh dấu là protected internal được truy cập
bởi các phương thức của lớp A, các phương thức của lớp dẫn xuất của A,
và bất cứ lớpnào trong cùng khối hợp ngữ của A.

Mong muốn chung là thiết kế các biến thành viên của lớp ở thuộc tính private. Khi đó
chỉ có phương thức thành viên của lớp truy cập được giá trị của biến. C# xem thuộc tính
private là mặc định nên ta không khai báo thuộc tính truy cập cho 6 biến nên mặc định
chúng là private:

// Các biến thành viên private int Nam; int Thang; int
Ngay; int Gio; int Phut; int Giay;

Do lớp Tester và phương thức thành viên ThoiGianHienHanh của lớp ThoiGian được
khai báo là public nên bất kỳ lớp nào cũng có thể truy cập được.

Ghi chú: Thói quen lập trình tốt là khai báo tường minh các thuộc tính truy cập của biến
thành viên hay các phương thức trong một lớp. Mặc dù chúng ta biết chắc chắn rằng các
thành viên của lớp là được khai báo private mặc định. Việc khai báo tường minh này sẽ
làm cho chương trình dễ hiểu, rõ ràng và tự nhiên hơn