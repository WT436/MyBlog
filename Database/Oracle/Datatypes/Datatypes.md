### Bảng tóm tắt Data Types của oracle :

|VARCHAR2|
| --- |

+ Syntax: `VARCHAR2(size [BYTE | CHAR])`
+ Description : Chuỗi ký tự có độ dài thay đổi có kích thước độ dài tối đa byte hoặc ký tự. Kích thước tối đa là 4000 byte hoặc ký tự, và tối thiểu là 1 byte hoặc 1 ký tự. Bạn phải chỉ định kích thước cho VARCHAR2. 
    - BYTE chỉ ra rằng column sẽ có ngữ nghĩa độ dài byte.
    - CHAR chỉ ra rằng column sẽ có ngữ nghĩa ký tự.

| NVARCHAR2 |
| --- |

+ Syntax: `NVARCHAR2(size)`
+ Description : Chuỗi ký tự Unicode có độ dài thay đổi có tối đa kích thước độ dài ký tự. Số byte có thể lên đến hai lần kích thước cho mã hóa AL16UTF16 và ba lần kích thước cho Mã hóa UTF8. Kích thước tối đa được xác định bởi quốc gia định nghĩa bộ ký tự, với giới hạn trên là 4000 byte. 
    - Bạn phải chỉ định kích thước cho NVARCHAR2.

| NUMBER |
| --- |

+ Syntax: `NUMBER[(precision [, scale]])`
+ Description : Số có độ chính xác p và thang đo s. 
    - precision có thể trong khoảng từ 1 đến 38. 
    - scale có thể nằm trong khoảng từ -84 đến 127.

| LONG |
| --- |

+ Syntax:  NULL
+ Description : Dữ liệu ký tự có độ dài thay đổi lên đến 2 gigabyte hoặc 231 -1
byte. Được cung cấp để tương thích ngược.

| DATE |
| --- |

+ Syntax: NULL
+ Description : Phạm vi ngày hợp lệ từ ngày 1 tháng 1 năm 4712 trước Công nguyên đến ngày 31 tháng 12 năm 9999 Sau công nguyên. 
    - Định dạng mặc định được xác định rõ ràng bởi tham số NLS_DATE_FORMAT hoặc ngầm định bởi tham số NLS_TERRITORY
    - Kích thước được cố định ở 7 byte. 
    - Kiểu dữ liệu này chứa các trường ngày giờ YEAR, MONTH, DAY, HOUR, MINUTE và SECOND.
    - Nó không có phân số giây hoặc múi giờ.

| BINARY_FLOAT |
| --- |

+ Syntax: NULL
+ Description : Số dấu phẩy động (NUMBER) 32-bit. Kiểu dữ liệu này yêu cầu 5 byte, bao gồm cả byte độ dài.

| BINARY_DOUBLE |
| --- |

+ Syntax: NULL
+ Description : Số dấu phẩy động (NUMBER) 64-bit. Kiểu dữ liệu này yêu cầu 9 byte, bao gồm cả byte độ dài.

| TIMESTAMP |
| --- |

+ Syntax: `TIMESTAMP [( fractional_seconds )]`
+ Description : Giá trị Year, month và day cũng như giờ, phút, và giây là giá trị của time, trong đó độ chính xác  fractional_seconds là số chữ số trong phần phân số của trường datetime thứ hai.
    - Fractional_seconds_pre precision nằm trong khoảng từ 0 đến 9. Giá trị mặc định của nó là 6.

    ```sql
    TIMESTAMP(0);   -- YYYY-MM-DD-hh-mm-ss
    TIMESTAMP(1);   -- YYYY-MM-DD-hh-mm-ss.f
    TIMESTAMP;      -- YYYY-MM-DD-hh-mm-ss.ffffff (Mặc định)
    TIMESTAMP(6);   -- YYYY-MM-DD-hh-mm-ss.ffffff
    TIMESTAMP(12);  -- YYYY-MM-DD-hh-mm-ss.ffffffffffff
    ```


+ Syntax: `TIMESTAMP [(fractional_seconds)] WITH TIME ZONE`
+ Description : Dữ liệu múi giờ có thể là độ lệch múi giờ, ví dụ: -07: 00, là sự khác biệt giữa giờ địa phương và giờ UTC hoặc tên khu vực múi giờ, ví dụ: Châu Âu / Luân Đôn

    ```sql
    TIMESTAMP '2017-08-09 07:00:00 -7:00' -- Châu Âu / Luân Đôn
    TIMESTAMP '15-JAN-99 08.00.00.000000000 AM ASIA/BANGKOK' -- đố biết ở đâu
    ```

| INTERVAL YEAR |
| --- |

+ Syntax: INTERVAL YEAR [(year_precision)] TO MONTH
+ Description : Lưu trữ một khoảng thời gian tính bằng năm và tháng, trong đó year_pre precision là số chữ số trong trường ngày giờ YEAR. Các giá trị được chấp nhận là 0 đến 9. Giá trị mặc định là 2. Kích thước được cố định ở 5 byte.

| INTERVAL DAY TO SECOND |
| --- |

+ Syntax: INTERVAL DAY [(day_precision)] TO SECOND [(fractional_seconds)]

+ Description : Lưu trữ một khoảng thời gian tính bằng ngày, giờ, phút và giây,
    - day_pre precision là số chữ số tối đa trong trường ngày giờ DAY. Các giá trị được chấp nhận là 0 đến 9. Giá trị mặc định
là 2.
    - fractional_seconds_preferences là số chữ số trong phần phân số của trường SECOND. Các giá trị được chấp nhận là 0 đến 9. Giá trị mặc định là 6.
    - Kích thước được cố định ở 11 byte.

| RAW |
| --- |

+ Syntax: RAW(size)
+ Description : Dữ liệu nhị phân RAW có kích thước chiều dài byte. Kích thước tối đa là 2000 byte. Bạn phải chỉ định kích thước cho một giá trị RAW.
    - `LONG RAW` : Có thể lên đến 2gb

| ROWID |
| --- |

+ Syntax: 
+ Description : Đối với mỗi hàng trong cơ sở dữ liệu, cột giả ROWID trả về địa chỉ của hàng. Các giá trị rowid của Cơ sở dữ liệu Oracle chứa thông tin cần thiết để định vị một hàng:
    - Số đối tượng dữ liệu của đối tượng
    - Khối dữ liệu trong tệp dữ liệu chứa hàng.
    - Vị trí của hàng trong khối dữ liệu (hàng đầu tiên là 0).
    - Tệp dữ liệu chứa hàng (tệp đầu tiên là 1). Số tệp có liên quan đến không gian bảng.
+ Thông thường, một giá trị rowid xác định duy nhất một hàng trong cơ sở dữ liệu. Tuy nhiên, các hàng trong các bảng khác nhau được lưu trữ cùng nhau trong cùng một cụm có thể có cùng một rowid. 
+ Giá trị Rowid có một số công dụng quan trọng:
    - Chúng là cách nhanh nhất để truy cập vào một hàng duy nhất.
    - Họ có thể chỉ cho bạn cách các hàng trong bảng được lưu trữ.
    - Chúng là số nhận dạng duy nhất cho các hàng trong bảng.
+ Bạn không nên sử dụng ROWID làm khóa chính của bảng. Ví dụ: nếu bạn xóa và chèn lại một hàng bằng các tiện ích Nhập và Xuất, thì rowid của hàng đó có thể thay đổi. Nếu bạn xóa một hàng, thì Oracle có thể gán lại rowid của nó cho một hàng mới được chèn sau đó.
+ Mặc dù bạn có thể sử dụng cột giả ROWID trong mệnh đề SELECT và WHERE của truy vấn, các giá trị cột giả này không thực sự được lưu trữ trong cơ sở dữ liệu. Bạn không thể chèn, cập nhật hoặc xóa giá trị của cột giả ROWID.

| ROWID | LAST_NAME |
| --- | --- |
| AAARyFAADAAACTVAAD	| Hartstein |
| AAARyFAADAAACTVAAE	| Fay |

| UROWID |
| --- |

+ Syntax: UROWID [(size)]
+ Description : Chuỗi base 64 đại diện cho địa chỉ lôgic của một hàng trong bảng được tổ chức theo chỉ mục. Kích thước tùy chọn là kích thước của một cột kiểu UROWID. Kích thước tối đa và mặc định là 4000 byte.

| CHAR |
| --- |

+ Syntax: CHAR [(size [BYTE | CHAR])]
+ Description : Dữ liệu ký tự có độ dài cố định có độ dài kích thước byte hoặc ký tự. Kích thước tối đa là 2000 byte hoặc ký tự. Kích thước mặc định và tối thiểu là 1 byte. BYTE và CHAR có cùng ngữ nghĩa như đối với VARCHAR2.

| NCHAR |
| --- |

+ Syntax: NCHAR[(size)]
+ Description : Dữ liệu ký tự có độ dài cố định của các ký tự có kích thước độ dài. Số lượng byte có thể gấp hai lần kích thước đối với mã hóa AL16UTF16 và gấp ba lần kích thước đối với mã hóa UTF8. Kích thước tối đa được xác định theo định nghĩa bộ ký tự quốc gia, với giới hạn trên 2000 byte. Kích thước mặc định và tối thiểu là 1 ký tự.

| CLOB |
| --- |

+ Syntax: 
+ Description : Một đối tượng lớn ký tự chứa các ký tự byte đơn hoặc nhiều byte. Cả hai bộ ký tự có độ rộng cố định và độ rộng thay đổi đều được hỗ trợ, cả hai đều sử dụng bộ ký tự cơ sở dữ liệu. Kích thước tối đa là (4 gigabyte - 1) * (kích thước khối cơ sở dữ liệu).

| NCLOB |
| --- |

+ Syntax: 
+ Description : Một đối tượng lớn ký tự chứa các ký tự Unicode. Cả hai bộ ký tự có độ rộng cố định và độ rộng thay đổi đều được hỗ trợ, cả hai đều sử dụng bộ ký tự quốc gia trong cơ sở dữ liệu. Kích thước tối đa là (4 gigabyte - 1) * (kích thước khối cơ sở dữ liệu). Lưu trữ dữ liệu bộ ký tự quốc gia.

| BLOB |
| --- |

+ Syntax: 
+ Description : Một đối tượng lớn nhị phân. Kích thước tối đa là (4 gigabyte - 1) * (kích thước khối cơ sở dữ liệu).

| BFILE |
| --- |

+ Syntax: 
+ Description : Chứa một bộ định vị đến một tệp nhị phân lớn được lưu trữ bên ngoài cơ sở dữ liệu. Cho phép truy cập I / O luồng byte vào các LOB bên ngoài nằm trên máy chủ cơ sở dữ liệu. Kích thước tối đa là 4 gigabyte.

...

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>