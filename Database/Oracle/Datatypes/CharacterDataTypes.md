### DataTypes Character

+ Các kiểu dữ liệu ký tự lưu trữ dữ liệu ký tự (chữ và số), là các từ và văn bản dạng tự do, trong bộ ký tự cơ sở dữ liệu hoặc bộ ký tự quốc gia. Chúng ít hạn chế hơn các kiểu dữ liệu khác và do đó có ít thuộc tính hơn. Ví dụ: các cột ký tự có thể lưu trữ tất cả các giá trị chữ và số, nhưng NUMBER cột chỉ có thể lưu trữ các giá trị số.

+ Dữ liệu ký tự được lưu trữ trong các chuỗi có giá trị byte tương ứng với một trong các bộ ký tự, chẳng hạn như ASCII hoặc EBCDIC 7-bit, được chỉ định khi cơ sở dữ liệu được tạo. Cơ sở dữ liệu Oracle hỗ trợ cả bộ ký tự byte đơn và nhiều byte.

+ Các kiểu dữ liệu này được sử dụng cho dữ liệu ký tự: 

    - CHAR Data Type
    - NCHAR Data Type
    - VARCHAR2 Data Type
    - NVARCHAR2 Data Type

| CHAR | 
|---|

- Kiểu dữ liệu CHAR chỉ định một chuỗi ký tự có độ dài cố định trong bộ ký tự cơ sở dữ liệu. Bạn chỉ định bộ ký tự cơ sở dữ liệu khi bạn tạo cơ sở dữ liệu của mình.

- Khi bạn tạo bảng có cột CHAR, bạn chỉ định độ dài cột làm kích thước theo tùy chọn, theo sau là bộ định lượng độ dài. Bộ định tính BYTE biểu thị ngữ nghĩa độ dài byte trong khi bộ định tính CHAR biểu thị ngữ nghĩa độ dài ký tự. Theo ngữ nghĩa độ dài byte, kích thước là số byte cần lưu trữ trong cột. Trong ngữ nghĩa độ dài ký tự, kích thước là số điểm mã trong bộ ký tự cơ sở dữ liệu để lưu trữ trong cột. Một điểm mã có thể có từ 1 đến 4 byte tùy thuộc vào bộ ký tự cơ sở dữ liệu và ký tự cụ thể được mã hóa bởi điểm mã. Oracle khuyến nghị rằng bạn chỉ định một trong các định mức độ dài để ghi rõ ràng ngữ nghĩa độ dài mong muốn của cột. Nếu bạn không chỉ định bộ định tính, giá trị của tham số NLS_LENGTH_SEMANTICS của phiên tạo cột xác định ngữ nghĩa độ dài, trừ khi bảng thuộc về lược đồ SYS, trong trường hợp đó ngữ nghĩa mặc định là BYTE.

- Oracle đảm bảo rằng tất cả các giá trị được lưu trữ trong cột CHAR có độ dài được chỉ định theo kích thước trong ngữ nghĩa độ dài đã chọn. Nếu bạn chèn một giá trị ngắn hơn độ dài cột, thì Oracle sẽ điền giá trị vào độ dài cột. Nếu bạn cố gắng chèn một giá trị quá dài cho cột, thì Oracle sẽ trả về một lỗi. Lưu ý rằng nếu độ dài cột được biểu thị bằng ký tự (điểm mã), thì phần đệm trống không đảm bảo rằng tất cả các giá trị cột có cùng độ dài byte.

- Bạn có thể bỏ qua kích thước khỏi định nghĩa cột. Giá trị mặc định là 1.

- Giá trị tối đa của kích thước là 2000, có nghĩa là 2000 byte hoặc ký tự (điểm mã), tùy thuộc vào ngữ nghĩa độ dài đã chọn. Tuy nhiên, một cách độc lập, độ dài tối đa tuyệt đối của bất kỳ giá trị ký tự nào có thể được lưu trữ vào cột CHAR là 2000 byte. Ví dụ: ngay cả khi bạn xác định độ dài cột là 2000 ký tự, Oracle vẫn trả về lỗi nếu bạn cố gắng chèn giá trị 2000 ký tự trong đó một hoặc nhiều điểm mã rộng hơn 1 byte. Giá trị của kích thước tính bằng ký tự là giới hạn về độ dài, không được đảm bảo về dung lượng. Nếu bạn muốn cột CHAR luôn có thể lưu trữ các ký tự kích thước trong bất kỳ bộ ký tự cơ sở dữ liệu nào, hãy sử dụng giá trị có kích thước nhỏ hơn hoặc bằng 500.

- Để đảm bảo chuyển đổi dữ liệu thích hợp giữa cơ sở dữ liệu và máy khách có các bộ ký tự khác nhau, bạn phải đảm bảo rằng dữ liệu CHAR bao gồm các chuỗi được định dạng tốt.

| NCHAR |
|---|

- Kiểu dữ liệu NCHAR chỉ định một chuỗi ký tự có độ dài cố định trong bộ ký tự quốc gia. Bạn chỉ định bộ ký tự quốc gia là AL16UTF16 hoặc UTF8 khi bạn tạo cơ sở dữ liệu của mình. AL16UTF16 và UTF8 là hai dạng mã hóa của bộ ký tự Unicode (tương ứng là UTF-16 và CESU-8) và do đó NCHAR là kiểu dữ liệu chỉ Unicode.

- Khi bạn tạo bảng có cột NCHAR, bạn chỉ định độ dài cột dưới dạng ký tự kích thước, hay chính xác hơn là các điểm mã trong bộ ký tự quốc gia. Một điểm mã luôn có 2 byte trong AL16UTF16 và từ 1 đến 3 byte trong UTF8, tùy thuộc vào ký tự cụ thể được mã hóa bởi điểm mã.

- Oracle đảm bảo rằng tất cả các giá trị được lưu trữ trong một cột NCHAR đều có độ dài bằng ký tự kích thước. Nếu bạn chèn một giá trị ngắn hơn độ dài cột, thì Oracle sẽ điền giá trị vào độ dài cột. Nếu bạn cố gắng chèn một giá trị quá dài cho cột, thì Oracle sẽ trả về một lỗi. Lưu ý rằng nếu bộ ký tự quốc gia là UTF8, thì phần đệm trống không đảm bảo rằng tất cả các giá trị cột có cùng độ dài byte.

- Bạn có thể bỏ qua kích thước khỏi định nghĩa cột. Giá trị mặc định là 1.

- Giá trị tối đa của kích thước là 1000 ký tự khi bộ ký tự quốc gia là AL16UTF16 và 2000 ký tự khi bộ ký tự quốc gia là UTF8. Tuy nhiên, một cách độc lập, độ dài tối đa tuyệt đối của bất kỳ giá trị ký tự nào có thể được lưu trữ vào cột NCHAR là 2000 byte. Ví dụ: ngay cả khi bạn xác định độ dài cột là 1000 ký tự, Oracle vẫn trả về lỗi nếu bạn cố gắng chèn giá trị 1000 ký tự nhưng bộ ký tự quốc gia là UTF8 và tất cả các điểm mã đều rộng 3 byte. Giá trị của kích thước là giới hạn về độ dài, không được đảm bảo về dung lượng. Nếu bạn muốn cột NCHAR luôn có thể lưu trữ các ký tự kích thước trong cả hai bộ ký tự quốc gia, hãy sử dụng giá trị có kích thước nhỏ hơn hoặc bằng 666.

- Để đảm bảo chuyển đổi dữ liệu thích hợp giữa cơ sở dữ liệu và máy khách có các bộ ký tự khác nhau, bạn phải đảm bảo rằng dữ liệu NCHAR bao gồm các chuỗi được định dạng tốt.

- Nếu bạn gán giá trị CHAR cho cột NCHAR, giá trị này được chuyển đổi ngầm định từ bộ ký tự cơ sở dữ liệu thành bộ ký tự quốc gia. Nếu bạn gán giá trị NCHAR cho cột CHAR, giá trị này được chuyển đổi ngầm định từ bộ ký tự quốc gia thành bộ ký tự cơ sở dữ liệu. Nếu một số ký tự từ giá trị NCHAR không thể được đại diện trong bộ ký tự cơ sở dữ liệu, thì nếu giá trị của tham số phiên NLS_NCHAR_CONV_EXCP là TRUE, thì Oracle sẽ báo lỗi. Nếu giá trị của tham số là FALSE, các ký tự không thể đại diện được thay thế bằng ký tự thay thế mặc định của bộ ký tự cơ sở dữ liệu, thường là dấu chấm hỏi '?' hoặc dấu hỏi đảo ngược '¿'.

| VARCHAR2  |
|---|

- Kiểu dữ liệu VARCHAR2 chỉ định một chuỗi ký tự có độ dài thay đổi trong bộ ký tự cơ sở dữ liệu. Bạn chỉ định bộ ký tự cơ sở dữ liệu khi bạn tạo cơ sở dữ liệu của mình.

- Khi bạn tạo bảng có cột VARCHAR2, bạn phải chỉ định độ dài cột làm kích thước tùy chọn, theo sau là bộ định lượng độ dài. Bộ định tính BYTE biểu thị ngữ nghĩa độ dài byte trong khi bộ định tính CHAR biểu thị ngữ nghĩa độ dài ký tự. Trong ngữ nghĩa độ dài byte, kích thước là số byte tối đa có thể được lưu trữ trong cột. Trong ngữ nghĩa độ dài ký tự, kích thước là số điểm mã tối đa trong bộ ký tự cơ sở dữ liệu có thể được lưu trữ trong cột. Một điểm mã có thể có từ 1 đến 4 byte tùy thuộc vào bộ ký tự cơ sở dữ liệu và ký tự cụ thể được mã hóa bởi điểm mã. Oracle khuyến nghị rằng bạn chỉ định một trong các định mức độ dài để ghi rõ ràng ngữ nghĩa độ dài mong muốn của cột. Nếu bạn không chỉ định bộ định tính, giá trị của tham số NLS_LENGTH_SEMANTICS của phiên tạo cột xác định ngữ nghĩa độ dài, trừ khi bảng thuộc về lược đồ SYS, trong trường hợp đó ngữ nghĩa mặc định là BYTE.

- Oracle lưu trữ giá trị ký tự trong cột VARCHAR2 chính xác như bạn chỉ định, không có bất kỳ khoảng đệm trống nào, miễn là giá trị không vượt quá độ dài của cột. Nếu bạn cố gắng chèn một giá trị vượt quá độ dài được chỉ định, thì Oracle sẽ trả về một lỗi.

- Giá trị nhỏ nhất của kích thước là 1. Giá trị lớn nhất là:

- 32767 byte nếu MAX_STRING_SIZE = EXTENDED
- 4000 byte nếu MAX_STRING_SIZE = STANDARD

- Tham khảo Kiểu dữ liệu mở rộng để biết thêm thông tin về tham số khởi tạo MAX_STRING_SIZE và cơ chế lưu trữ nội bộ cho kiểu dữ liệu mở rộng.

- Trong khi kích thước có thể được biểu thị bằng byte hoặc ký tự (điểm mã) thì độ dài tối đa tuyệt đối độc lập của bất kỳ giá trị ký tự nào có thể được lưu trữ vào cột VARCHAR2 là 32767 hoặc 4000 byte, tùy thuộc vào MAX_STRING_SIZE. Ví dụ: ngay cả khi bạn xác định độ dài cột là 32767 ký tự, Oracle vẫn trả về lỗi nếu bạn cố gắng chèn giá trị 32767 ký tự trong đó một hoặc nhiều điểm mã rộng hơn 1 byte. Giá trị của kích thước tính bằng ký tự là giới hạn về độ dài, không được đảm bảo về dung lượng. Nếu bạn muốn cột VARCHAR2 luôn có thể lưu trữ các ký tự kích thước trong bất kỳ bộ ký tự cơ sở dữ liệu nào, hãy sử dụng giá trị có kích thước nhỏ hơn hoặc bằng 8191, nếu MAX_STRING_SIZE = EXTENDED hoặc 1000, nếu MAX_STRING_SIZE = STANDARD.

- Oracle so sánh các giá trị VARCHAR2 bằng cách sử dụng ngữ nghĩa so sánh không đệm.

| VARCHAR  |
|---|

- Không sử dụng kiểu dữ liệu VARCHAR. Sử dụng kiểu dữ liệu VARCHAR2 để thay thế. Mặc dù kiểu dữ liệu VARCHAR hiện đồng nghĩa với VARCHAR2, nhưng kiểu dữ liệu VARCHAR được lên lịch để định nghĩa lại thành kiểu dữ liệu riêng biệt được sử dụng cho các chuỗi ký tự có độ dài thay đổi so với các ngữ nghĩa so sánh khác nhau.

| NVARCHAR2  | 
|---|

- Kiểu dữ liệu NVARCHAR2 chỉ định một chuỗi ký tự có độ dài thay đổi trong bộ ký tự quốc gia. Bạn chỉ định bộ ký tự quốc gia là AL16UTF16 hoặc UTF8 khi bạn tạo cơ sở dữ liệu của mình. AL16UTF16 và UTF8 là hai dạng mã hóa của bộ ký tự Unicode (tương ứng là UTF-16 và CESU-8) và do đó NVARCHAR2 là kiểu dữ liệu chỉ Unicode.

- Khi bạn tạo một bảng với cột NVARCHAR2, bạn phải chỉ định độ dài cột dưới dạng các ký tự kích thước, hay chính xác hơn là các điểm mã trong bộ ký tự quốc gia. Một điểm mã luôn có 2 byte trong AL16UTF16 và từ 1 đến 3 byte trong UTF8, tùy thuộc vào ký tự cụ thể được mã hóa bởi điểm mã.

- Oracle lưu trữ giá trị ký tự trong cột NVARCHAR2 chính xác như bạn chỉ định, không có bất kỳ khoảng đệm trống nào, miễn là giá trị không vượt quá độ dài của cột. Nếu bạn cố gắng chèn một giá trị vượt quá độ dài được chỉ định, thì Oracle sẽ trả về một lỗi.

+ Giá trị nhỏ nhất của kích thước là 1. Giá trị lớn nhất là:

    - 16383 nếu MAX_STRING_SIZE = EXTENDED và bộ ký tự quốc gia là AL16UTF16
    - 32767 nếu MAX_STRING_SIZE = EXTENDED và bộ ký tự quốc gia là UTF8
    - 2000 nếu MAX_STRING_SIZE = STANDARD và bộ ký tự quốc gia là AL16UTF16
    - 4000 nếu MAX_STRING_SIZE = STANDARD và bộ ký tự quốc gia là UTF8

+ Tham khảo Kiểu dữ liệu mở rộng để biết thêm thông tin về tham số khởi tạo MAX_STRING_SIZE và cơ chế lưu trữ nội bộ cho kiểu dữ liệu mở rộng.

+ Không phụ thuộc vào độ dài cột tối đa tính bằng ký tự, độ dài tối đa tuyệt đối của bất kỳ giá trị nào có thể được lưu trữ vào cột NVARCHAR2 là 32767 hoặc 4000 byte, tùy thuộc vào MAX_STRING_SIZE. Ví dụ: ngay cả khi bạn xác định độ dài cột là 16383 ký tự, Oracle vẫn trả về lỗi nếu bạn cố gắng chèn giá trị 16383 ký tự nhưng bộ ký tự quốc gia là UTF8 và tất cả các điểm mã đều rộng 3 byte. Giá trị của kích thước là giới hạn về độ dài, không được đảm bảo về dung lượng. Nếu bạn muốn cột NVARCHAR2 luôn có thể lưu trữ các ký tự kích thước trong cả hai bộ ký tự quốc gia, hãy sử dụng giá trị có kích thước nhỏ hơn hoặc bằng 10922, nếu MAX_STRING_SIZE = EXTENDED hoặc 1333, nếu MAX_STRING_SIZE = STANDARD.

+ Oracle so sánh các giá trị NVARCHAR2 bằng cách sử dụng ngữ nghĩa so sánh không đệm.

+ Để đảm bảo chuyển đổi dữ liệu thích hợp giữa cơ sở dữ liệu và máy khách có các bộ ký tự khác nhau, bạn phải đảm bảo rằng dữ liệu NVARCHAR2 bao gồm các chuỗi được định dạng tốt.

+ Nếu bạn gán giá trị VARCHAR2 cho cột NVARCHAR2, giá trị này được chuyển đổi ngầm định từ bộ ký tự cơ sở dữ liệu thành bộ ký tự quốc gia. Nếu bạn gán giá trị NVARCHAR2 cho cột VARCHAR2, giá trị này được chuyển đổi ngầm định từ bộ ký tự quốc gia thành bộ ký tự cơ sở dữ liệu. Nếu một số ký tự từ giá trị NVARCHAR2 không thể được đại diện trong bộ ký tự cơ sở dữ liệu, thì nếu giá trị của tham số phiên NLS_NCHAR_CONV_EXCP là TRUE, thì Oracle sẽ báo lỗi. Nếu giá trị của tham số là FALSE, các ký tự không thể đại diện được thay thế bằng ký tự thay thế mặc định của bộ ký tự cơ sở dữ liệu, thường là dấu chấm hỏi '?' hoặc dấu hỏi đảo ngược '¿'.

-- Nguồn : Oracle
<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>