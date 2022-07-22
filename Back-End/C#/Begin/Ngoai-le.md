# Phát sinh và bắt giữ ngoại lệ

- Một điều quan trọng để phân chia giữa bug, lỗi, và ngoại lệ. Một bug là một lỗi lập trình có thể được sửa chữa trước khi mã nguồn được chuyển giao. Những ngoại lệ thì không được bảo vệ và tương phản với những bug. Mặc dù một bug có thể là nguyên nhân sinh ra ngoại lệ, chúng ta cũng không dựa vào những ngoại lệ để xử lý những bug trong chương trình, tốt hơn là chúng ta nên sửa chữa những bug này.
- Một lỗi có nguyên nhân là do phía hành động của người sử dụng. Ví dụ, người sử dụng nhập vào một số nhưng họ lại nhập vào ký tự chữ cái. Một lần nữa, lỗi có thể làm xuất hiện ngoại lệ, nhưng chúng ta có thể ngăn ngừa điều này bằng cách bắt giữ lỗi với mã hợp lệ. Những lỗi có thể được đoán trước và được ngăn ngừa.

## Câu lệnh throw

- Để phát tín hiệu một sự không bình thường trong một lớp của ngôn ngữ C#, chúng ta phát sinh một ngoại lệ. Để làm được điều này, chúng ta sử dụng từ khóa throw. Dòng lệnh sau tạo ra một thể hiện mới của System.Exception và sau đó throw nó: throw new System.Exception();
- Khi phát sinh ngoại lệ thì ngay tức khắc sẽ làm ngừng việc thực thi trong khi CLR sẽ tìm kiếm một trình xử lý ngoại lệ. Nếu một trình xử lý ngoại lệ không được tìm thấy trong phương thức hiện thời, thì CLR tiếp tục tìm trong phương thức gọi cho đến khi nào tìm thấy. Nếu CLR trả về lớp Main() mà không tìm thấy bất cứ trình xử lý ngoại lệ nào, thì nó sẽ kết thúc chương trình.

## Câu lệnh catch

- Trong C#, một trình xử lý ngoại lệ hay một đoạn chương trình xử lý các ngoại lệ được gọi là một khối catch và được tạo ra với từ khóa catch.

## Câu lệnh finally

- Trong một số tình huống, việc phát sinh ngoại lệ và unwind stack có thể tạo ra một số vấn đề. Ví dụ như nếu chúng ta mở một tập tin hay trường hợp khác là xác nhận một tài nguyên, chúng ta có thể cần thiết một cơ hội để đóng một tập tin hay là giải phóng bộ nhớ đệm mà chương trình đã chiếm giữ trước đó.
- Trong ngôn ngữ C#, vấn đề này ít xảy ra hơn do cơ chế thu dọn tự động của C# ngăn ngừa những ngoại lệ phát sinh từ việc thiếu bộ nhớ.
- Tuy nhiên, có một số hành động mà chúng ta cần phải quan tâm bất cứ khi nào một ngoại lệ được phát sinh ra, như việc đóng một tập tin, chúng ta có hai chiến lược để lựa chọn thực hiện. Một hướng tiếp cận là đưa hành động nguy hiểm vào trong khối try và sau đó thực hiện việc đóng tập tin trong cả hai khối catch và try.
- Tuy nhiên, điều này gây ra đoạn chương trình không được đẹp do sử dụng trùng lắp lệnh. Ngôn ngữ C# cung cấp một sự thay thế tốt hơn trong khối finally.

# Những đối tượng ngoại lệ

- Đối tượng System.Exception cung cấp một số các phương thức và thuộc tính hữu dụng. Thuộc tính Message cung cấp thông tin về ngoại lệ, như là lý do tại sao ngoại lệ được phát sinh. Thuộc tính Message là thuộc tính chỉ đọc, đoạn chương trình phát sinh ngoại lệ có thể thiết lập thuộc tính Message như là một đối mục cho bộ khởi dựng của ngoại lệ.
- Thuộc tính HelpLink cung cấp một liên kết để trợ giúp cho các tập tin liên quan đến các ngoại lệ. Đây là thuộc tính chỉ đọc. Thuộc tính StackTrace cũng là thuộc tính chỉ đọc và được thiết lập bởi CLR. thuộc tính Exception.HelpLink được thiết lập và truy cập để cung cấp thông tin cho người sử dụng về ngoại lệ DivideByZeroException. Thuộc tính StackTrace của ngoại lệ được sử dụng để cung cấp thông tin stack cho câu lệnh lỗi.
- Một thông tin stack cung cấp hàng loạt các cuộc gọi stack của phương thức gọi mà dẫn đến những ngoại lệ được phát sinh.

### Các ngoại lệ thường xuất hiện

- MethodAccessException : Lỗi truy cập, do truy cập đến thành viên hayphương thức không được truy cập
- ArgumentException : Lỗi tham số đối mục
- ArgumentNullException : Đối mục Null, phương thức được truyền đối mụcnull không được chấp nhận
- ArithmeticException : Lỗi liên quan đến các phép toán
- ArrayTypeMismatchException : Kiểu mảng không hợp, khi cố lưu trữ kiểu khôngthích hợp vào mảng
- DivideByZeroException : Lỗi chia zero
- FormatException : Định dạng không chính xác một đối mục nào đó
- IndexOutOfRangeException : Chỉ số truy cập mảng không hợp lệ, dùng nhỏ hơn chỉ số nhỏ nhất hay lớn hơn chỉ số lớn nhất của mảng
- InvalidCastException : Phép gán không hợp lệ
- MulticastNotSupportedException : Multicast không được hỗ trợ, do việc kết hợp haidelegate không đúng
- NotFiniteNumberException : Không phải số hữu hạn, số không hợp lệ
- NotSupportedException : Phương thức không hỗ trợ, khi gọi một phươngthức không tồn tại bên trong lớp.
- NullReferenceException : Tham chiếu null không hợp lệ.
- OutOfMemoryException : Out of memory
- OverflowException : Lỗi tràn phép toán
- StackOverflowException : Tràn stack
- TypeInitializationException : Kiểu khởi tạo sai, khi bộ khởi dựng tĩnh có lỗi.

### Tạo riêng các ngoại lệ

- CLR cung cấp những kiểu dữ liệu ngoại lệ cơ bản, trong ví dụ trước chúng ta đã tạo một vài các kiểu ngoại lệ riêng. Thông thường chúng ta cần thiết phải cung cấp các thông tin mở rộng cho khối catchkhi một ngoại lệ được phát sinh. Tuy nhiên, có những lúc chúng ta muốn cung cấp nhiều thông tin mở rộng hay là các khả năng đặc biệt cần thiết trong ngoại lệ mà chúng ta tạo ra. Chúng ta dễ dàng tạo ra các ngoại lệ riêng, hay còn gọi là các ngoại lệ tùy chọn (custom exception), điều bắt buộc với các ngoại lệ này là chúng phải được dẫn xuất từ System.ApplicationException.
