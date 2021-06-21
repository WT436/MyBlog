# Lớp đối tượng String

Lớp string cung cấp rất nhiều số lượng các phương thức để so sánh, tìm kiếm và thao tác trên chuỗi, các phương thức này được trình bày trong bảng sau:

- Empty : Trường public static thể hiện một chuỗi rỗng.
- Compare() : Phương thức public static để so sánh hai chuỗi.
- CompareOrdinal() : Phương thức public static để so sánh hai chuỗi khôngquan tâm đến thứ tự.
- Concat() : Phương thức public static để tạo chuỗi mới từ một haynhiều chuỗi.
- Copy() : Phương thức public static tạo ra một chuỗi mới bằngsao từ chuỗi khác.
- Equal() : Phương thức public static kiểm tra xem hai chuỗi cócùng giá trị hay không.
- Format() : Phương thức public static định dạng một chuỗi dùngký tự lệnh định dạng xác định.
- Intern() : Phương thức public static trả về tham chiếu đến thểhiện của chuỗi.
- IsInterned() : Phương thức public static trả về tham chiếu của chuỗi
- Join() : Phương thức public static kết nối các chuỗi xác địnhgiữa mỗi thành phần của mảng chuỗi.
- Chars() : Indexer của chuỗi.
- Length() : Chiều dài của chuỗi.
- Clone() : Trả về chuỗi.
- CompareTo() : So sánh hai chuỗi.
- CopyTo() : Sao chép một số các ký tự xác định đến một mảng kýtự Unicode.
- EndsWidth() : Chỉ ra vị trí của chuỗi xác định phù hợp với chuỗi đưara.
- Insert() : Trả về chuỗi mới đã được chèn một chuỗi xác định.
- LastIndexOf() : Chỉ ra vị trí xuất hiện cuối cùng của một chuỗi xácđịnh trong chuỗi.
- PadLeft() : Canh lề phải những ký tự trong chuỗi, chèn vào bêntrái khoảng trắng hay các ký tự xác định.
- PadRight() : Canh lề trái những ký tự trong chuỗi, chèn vào bênphải khoảng trắng hay các ký tự xác định.
- Remove() : Xóa đi một số ký tự xác định.
- Split() : Trả về chuỗi được phân định bởi những ký tự xác địnhtrong chuỗi.
- StartWidth() : Xem chuỗi có bắt đầu bằng một số ký tự xác định haykhông.
- SubString() : Lấy một chuỗi con.
- ToCharArray() : Sao chép những ký tự từ một chuỗi đến mảng ký tự.
- ToLower() : Trả về bản sao của chuỗi ở kiểu chữ thường.
- ToUpper() : Trả về bản sao của chuỗi ở kiểu chữ hoa.
- Trim() : Xóa bỏ tất cả sự xuất hiện của tập hợp ký tự xác định từ vị trí đầu tiên đến vị trí cuối cùng trong chuỗi.
- TrimEnd() : Xóa như nhưng ở vị trí cuối.
- TrimStart() : Xóa như Trim nhưng ở vị trí đầu

2. Thao tác trên chuỗi dùng StringBuilder
   - Lớp StringBuilder được sử dụng để tạo ra và bổ sung các chuỗi. Hay có thể nói lớp này chính là phần đóng gói của 
   - một bộ khởi dựng cho một String. Một số thành viên quan trọng StringBuilder được tóm tắt trong bảng như sau:
   - Capacity() : Truy cập hay gán một số ký tự mà StringBuilder nắm giữ.
   - Chars() : Chỉ mục.
   - Length() : Thiết lập hay truy cập chiều dài của chuỗi
   - MaxCapacity() : Truy cập dung lượng lớn nhất của StringBuilder
   - Append() : Nối một kiểu đối tượng vào cuối của StringBuilder
   - AppendFormat() : Thay thế định dạng xác định bằng giá trị được định dạngcủa một đối tượng.
   - EnsureCapacity() : Đảm bảo rằng StringBuilder hiện thời có khả năng tối thiểulớn như một giá trị xác định.
   - Insert() : Chèn một đối tượng vào một vị trí xác định
   - Replace() : Thay thế tất cả thể hiện của một ký tự xác định với nhữngký tự mới.
   Không giống như String, StringBuilder thì dễ thay đổi. Khi chúng ta bổ sung một đối tượng StringBuilder thì chúng ta đã làm thay đổi trên giá trị thật của chuỗi, chứ không phải trên bản sao.
