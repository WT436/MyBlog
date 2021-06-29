# KIểu Dữ liệu trong sql server

1. CHAR(kich_thuoc) Tối đa 8000 kí tự.

- kich_thuoc là số kí tự lưu trữ.
- Độ dài cố định.
- Thêm dấu cách về bên phải để bù phần trống cho đủ số kí tự.
- Không chứa kí tự Unicode.

2. VARCHAR(kich_thuoc) hoặc VARCHAR(toi_da) Tối đa 8000 kí tự hoặc theo số tối đa.

- kich_thuoc là số kí tự lưu trữ.
- Độ dài tùy biến.
- Nếu chỉ định là toi_da thì tối đa là 2GB.
- Không chứa kí tự Unicode.

3. TEXT Tối đa 2GB.

- Độ dài tùy biến.
- Không chứa kí tự Unicode.

4. NCHAR(kich_thuoc) Tối đa 4000 kí tự.

- Độ dài cố định.
- Kí tự Unicode.

5. NVARCHAR(kich_thuoc) hoặc NVARCHAR(toi_da) Tối đa 4000 kí tự hoặc theo số tối đa.

- kich_thuoc là số kí tự lưu trữ.
- Độ dài tùy biến.
- Nếu số toi_da được chi định thì số kí tự tối đa là 2GB.
- Kí tự Unicode.

6. NTEXT Tối đa 1.073.741.823 byte.

- Độ dài tùy biến.
- Kí tự Unicode.

7. BINARY(kich_thuoc) Tối đa 8000 kí tự.
   kich_thuoc là số kí tự lưu trữ.

- Độ dài cố định.
- Thêm dấu cách để bù phần trống cho đủ số kí tự.
- Dữ liệu nhị phân.

8. VARBINARY(kich_thuoc) hoặc VARBINARY(toi_da) Tối đa 8000 kí tự hoặc theo số tối đa.

- kich_thuoc là số kí tự lưu trữ.
- Độ dài tùy biến.
- Nếu chỉ định là toi_da thì tối đa là 2GB.
- Dữ liệu nhị phân.

9. MAGE kích thước tối đa là 2GB.

- Độ dài tùy biến.
- Dữ liệu nhị phân.

10. BIT số nguyên 0, 1 hoặc NULL
11. TINYINT từ 0 đến 255
12. SMALLINT từ -32768 đến 32767
13. INT -2,147,483,648 đến 2,147,483,647
14. BIGINT từ -9,223,372,036,854,775,808 đến 9,223,372,036,854,775,807
15. DECIMAL(m,d)
    m mặc định là 18 nếu không được chỉ định cụ thể.

- d mặc định là 0 nếu không được chỉ định cụ thể.
- m là tổng số lượng các số còn d là số lượng các số nằm sau dấu phẩy.

16. DEC(m,d)

- m mặc định là 18 nếu không được chỉ định cụ thể.
- d mặc định là 0 nếu không được chỉ định cụ thể.
- m là tổng số lượng các số còn d là số lượng các số nằm sau dấu phẩy.
- Đồng nghĩa với kiểu dữ liệu DECIMAL.

17. NUMERIC(m,d)

- m mặc định là 18 nếu không được chỉ định cụ thể.
- d mặc định là 0 nếu không được chỉ định cụ thể.
- m là tổng số lượng các số còn d là số lượng các số nằm sau dấu phẩy.
- Đồng nghĩa với kiểu dữ liệu DECIMAL.

18. FLOAT(n) số dấu phẩy động n mặc định là 53 nếu không được chỉ định cụ thể.

- n là số lượng của số bit lưu trữ trong một kí hiệu hóa học.

19. REAL tương đương với FLOAT(24)
20. SMALLMONEY từ - 214,748.3648 đến 214,748.3647
21. MONEY từ -922,337,203,685,477.5808 đến 922,337,203,685,477.5807
22. DATE giá trị từ '0001-01-01' đến '9999-12-31. hiển thị dưới dạng ‘YYYY-MM-DD’
23. DATETIME

- Ngày lấy từ '1753-01-01 00:00:00' to '9999-12-31 23:59:59'.
- Giờ lấy từ '00:00:00' to '23:59:59:997'hiển thị dưới dạng ‘YYYY-MM-DD hh:mm:ss[.mmm]

24. DATETIME2(chính xác tới số thập phân của giây) giá trị lấy từ '0001-01-01' đến '9999-12-31'.

- Thời gian lấy từ '00:00:00' đến '23:59:59:9999999'.hiển thị dưới dạng 'YYYY-MM-DD hh:mm:ss[.số giây thập phân]'

25. SMALLDATETIME giá trị lấy từ '1900-01-01' đến '2079-06-06'.

- Thời gian lấy từ '00:00:00' đến '23:59:59'.hiển thị dưới dạng 'YYYY-MM-DD hh:mm:ss

26. TIME giá trị lấy từ '00:00:00.0000000' đến '23:59:59.9999999'.

- Ngày lấy từ '0001-01-01' đến '9999-12-31'. hiển thị dưới dạng 'YYYY-MM-DD hh:mm:ss[.nnnnnnn]'

27. DATETIMEOFFSET (chính xác tới số thập phân của giây) giá trị thời gian lấy từ '00:00:00' đến '23:59:59:9999999'.

- Múi giờ lấy từ -14:00 đến +14:00. hiển thị dưới dạng YYYY-MM-DD hh:mm:ss[.nnnnnnn]' [{+|-}hh:mm]
