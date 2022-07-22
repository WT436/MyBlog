# Làm việc với File dữ liệu

## Luồng nhập xuất

- Thuật ngữ tập tin thì nói chung là liên quan đến những thông tin lưu trữ bên trong ỗ đĩa hoặc trong bộ nhớ. Khi làm việc với tập tin, chúng ta bao hàm với việc sử dụng một luồng.
- Nhiều người nhầm lẫn về sự khác nhau giữa tập tin và luồng. Một luồng đơn giản là luồng của thông tin, chứa thông tin sẽ được chuyển qua, còn tập tin thì để lưu trữ thông tin.
- Một luồng được sử dụng để gởi và nhận thông tin từ bộ nhớ, từ mạng, web, từ một chuỗi,...Một luồng còn được sử dụng để đi vào và ra với một tập tin dữ liệu

### Thứ tự của việc đọc một tập tin

- Khi đọc hay viết một tập tin, cần thiết phải theo một trình tự xác định. Đầu tiên là phải thực hiện công việc mở tập tin. Nếu như tạo mới tập tin, thì việc mở tập tin cùng lúc với việc tạo ra tập tin đó. Khi một tập tin đã mở, cần thiết phải tạo cho nó một luồng để đặt thông tin vào trong một tập tin hay là lấy thông tin ra từ tập tin.
- Khi tạo một luồng, cần thiết phải chỉ ra thông tin trực tiếp sẽ được đi qua luồng. Sau khi tạo một luồng gắn với một tập tin, thì lúc này chúng ta có thể thực hiện việc đọc ghi các dữ liệu trên tập tin.
- Khi thực hiện việc đọc thông tin từ một tập tin, chúng ta cần thiết phải kiểm tra xem con trỏ tập tin đã chỉ tới cuối tập tin chưa, tức là chúng ta đã đọc đến cuối tập tin hay chưa.
- Khi hoàn thành việc đọc ghi thông tin trên tập tin thì tập tin cần phải được đóng lại.
- Tóm lại các bước cơ bản để làm việc với một tậo tin là:
  • Bước 1: Mở hay tạo mới tập tin
  • Bước 2: Thiết lập một luồng ghi hay đọc từ tập tin
  • Bước 3: Đọc hay ghi dữ liệu lên tập tin
  • Bước 4: Đóng lập tin lại

### Các phương thức cho việc tạo và mở tập tin

- Có nhiều kiểu luồng khác nhau. Chúng ta sẽ sử dụng những luồng khác nhau và những phương thức khác nhau phụ thuộc vào kiểu dữ liệu bên trong của tập tin. Trong phần này, việc đọc/ghi sẽ được thực hiện trên tập tin văn bản. Trong phần kế tiếp chúng ta học cách đọc và viết thông tin trên tập tin nhị phân. Thông tin nhị phân bao hàm khả năng mạnh lưu trữ giá trị số và bất cứ kiểu dữ liệu nào khác.
- Để mở một tập tin trên đĩa cho việc đọc và viết tập tin văn bản, chúng ta cần phải sử dụng cả hai lớp File và FileInfo. Một vài phương thức có thể sử dụng trong những lớp này. Các phương thức này bao gồm:
- AppendText: Mở một tập tin để và tập tin này có thể được thêm văn bản vào trong nó.
- Tạo luồng StreamWriter sử dụng để thêm vào trong văn bản.
- Create: Tạo mới một tập tin
- CreateText: Tạo và mở một tập tin văn bản. Tạo ra một luồng StreamWriter.
- Open: Mở một tập tin để đọc/viết. Mở một FileStream
- OpenRead: Mở một tập tin để đọc
- OpenText: Mở một tập tin văn bản để đọc. Tạo ra StreamReader để sử dụng.
- OpenWrite: Mở một tập tin cho việc đọc và ghi.
- Làm thế nào để chúng ta có thể biết được khi nào sử dụng lớp File chính xác hơn là sử dụng lớp FileInfo nếu chúng cùng chứa những phương thức tương tự với nhau. Thật ra hai lớp này có nhiều sự khác biệt. Lớp File chứa tất cả các phương thức tĩnh, thêm vào đó lớp File tự động kiểm tra permission trên một tập tin. Trong khi đó nếu muốn dùng lớp FileInfo thì phải tạo thể hiện của lớp này. Nếu muốn mở một tập tin chỉ một lần thì tốt nhất là sử dụng lớp File, còn nếu chúng ta tổ chức việc sử dụng tập tin nhiều lần bên trong chương trình, tốt nhất là ta dùng lớp FileInfo. Hoặc nếu không chắc chắn cách sử dụng thì chúng ta có thể sử dụng lớp FileInfo

- Bảng sau liệt kê những mode giá trị khác trong kiểu liệt kê FileMode.
- Append Mở một tập tin hiện hữu hoặc tạo một tập tin mới
- Create Tạo một tập tin mới. Nếu một tập tin đã hiện hữu, nó sẽ bị xóa và một tập tin mới sẽ được tạo ra với cùng tên.
- CreateNew Tạo một tệp tin mới.Nếu mội tập tin đã tồn tại thì một ngoại lệ sẽ được phát sinh.
- Open Mở tập tin hiện hữu.
- OpenOrCreate Mở tập tin hay tạo tập tin mới nếu tập tin chưa tồn tại
- Truncate Mở một tập tin hiện hữu và xóa nội dung của nó.

### Bảng sau liệt kê một số phương thức dùng để đọc các kiểu dữ liệu.

- Read : Đọc những ký tự và chuyển vị trí đọc sang vị trí tiếp theo.Phương thức này được nạp chồng gồm 3 phương thức.
- ReadBoolean : Đọc một giá trị boolean từ luồng hiện thời và chuyển vị trí đọcsang một byte.
- ReadByte : Đọc byte kế tiếp từ luồng hiện thời và chuyển vị trí đọc sang 1byte.
- ReadBytes : Đọc n byte từ luồng hiện thời sang một mảng byte và chuyển vịtrí đọc sang n byte.
- ReadChar : Đọc vị trí kế tiếp trong luồng hiện hành và chuyển vị trí đọc của luồng theo sau sử dụng mã hóa và ký tự xác định được đọc từluồng.
- ReadChars : Đọc n ký tự từ luồng hiện hành vào một mảng n ký tự. Và chuyển vị trí đọc của luồng theo sau sử dụng mã hóa và ký tự xác định được đọc từ luồng.
- ReadDecimal : Đọc giá trị decimal và chuyển vị trí đọc sang 16 byte.
- ReadDouble : Đọc giá trị thực 8 byte và chuyển vị trí đọc sang 8 byte.
- ReadInt16 : Đọc giá trị 2 byte integer có dấu và chuyển vị trí đọc sang 2 byte.
- ReadInt32 : Đọc giá trị 4 byte integer có dấu và chuyển vị trí đọc sang 4 byte.
- ReadInt64 : Đọc giá trị 8 byte integer có dấu và chuyển vị trí đọc sang 8 byte
- ReadSByte : Đọc một signed byte từ luồng và chuyển vị trí đọc sang 1 byte.
- ReadSingle : Đọc giá trị thực 4 byte từ luồng và chuyển vị trí đọc sang 4 byte.
- ReadString : Đọc một chuỗi từ luồng. Chuỗi được cố định chiều dài trước.Và được mã hóa mỗi lần như là số nguyên 7 bit.
- ReadUInt16 : Đọc giá trị 2-byte unsigned integer từ luồng. Sử dụng mã hóa thứ tự nhỏ ở cuối (little endian encoding). Và chuyển vị trí hiệnhành sang 2 byte.
- ReadUInt64 : Đọc 8-byte unsigned integer từ luống hiện hành và chuyển sang8 byte.
