# Danh Sách Lặt Vặt

1. MIN()

- Hàm MIN () trả về giá trị nhỏ nhất của cột đã chọn.

```sql
SELECT MIN(Tên cột)
FROM Tên Bảng
WHERE Điều Kiện;
```

2. Max()

- Hàm MAX () trả về giá trị Lớn nhất của cột đã chọn.

```sql
SELECT MAX(Tên cột)
FROM Tên Bảng
WHERE Điều Kiện;
```

3. COUNT()

- Hàm COUNT () trả về số hàng phù hợp với tiêu chí được chỉ định.

```sql
SELECT COUNT(Tên cột)
FROM Tên Bảng
WHERE Điều Kiện;

```

4. AVG

- Hàm AVG () trả về giá trị trung bình của một cột số.

```sql
SELECT AVG(Tên cột)
FROM Tên Bảng
WHERE Điều Kiện;

```

5. SUM()

- Hàm SUM () trả về tổng tổng của một cột số.

```sql
SELECT SUM(Tên cột)
FROM Tên Bảng
WHERE Điều Kiện;

```

6. IN

- Toán tử IN cho phép bạn chỉ định nhiều giá trị trong mệnh đề WHERE.
- Toán tử IN là cách viết tắt của nhiều điều kiện OR.

```sql
SELECT Tên cột(s)
FROM Bảng
WHERE Tên cột IN (value1, value2, ...);
```

7. LIKE

- Toán tử LIKE được sử dụng trong mệnh đề WHERE để tìm kiếm một mẫu được chỉ định trong một cột.
- Có hai ký tự đại diện thường được sử dụng cùng với toán tử LIKE: % -
- Dấu phần trăm đại diện cho không, một hoặc nhiều ký tự \_ \- Dấu gạch dưới thể hiện một ký tự

```sql
SELECT Cột 1, Cột 2, ...
FROM Bảng
WHERE Cột N LIKE Chuỗi cần Tìm;
```

Bảng Sau Mô Tả cách sử Dụng

- LIKE 'a%' Tìm bất kỳ giá trị nào bắt đầu bằng "a"
- LIKE '%a' Tìm bất kỳ giá trị nào kết thúc bằng "a"
- LIKE '%or%' Tìm bất kỳ giá trị nào có "a" ở bất kỳ vị trí nào
- LIKE '\_r%' Tìm bất kỳ giá trị nào có "r" ở vị trí thứ hai
- LIKE 'a\_%' Tìm bất kỳ giá trị nào bắt đầu bằng "a" và có ít nhất 2 ký tự
- LIKE 'a\_\_%' Tìm bất kỳ giá trị nào bắt đầu bằng "a" và có độ dài ít nhất 3 ký tự
- LIKE 'a%o' Tìm bất kỳ giá trị nào bắt đầu bằng "a" và kết thúc bằng "o"

8. Ký tự đại diện

% Đại diện cho không hoặc nhiều ký tự
\_ Đại diện cho một ký tự
[] Đại diện cho bất kỳ ký tự đơn nào trong dấu ngoặc
^ Đại diện cho bất kỳ ký tự nào không có trong dấu ngoặc
\- Đại diện cho một loạt các ký tự

9. BETWEEN

- Toán tử BETWEEN chọn các giá trị trong một phạm vi nhất định.
- Các giá trị có thể là số, văn bản hoặc ngày tháng.
- Toán tử BETWEEN được bao gồm: giá trị bắt đầu và kết thúc được bao gồm.

```sql
SELECT Tên cột(s)
FROM Bảng
WHERE Tên cột BETWEEN Giá trị 1 AND Giá trị 2;

```

10. AS (Bí Danh)

- Bí danh thường được sử dụng để làm cho tên cột dễ đọc hơn.
- Bí danh chỉ tồn tại trong thời gian truy vấn.

```sql
SELECT Tên cột (s)
FROM Tên Bảng AS Tên Bảng Hiển thị ra;
--Hoặc
SELECT Tên cột as Tên cột Hiển thị ra from Bảng
-- ..........

```

11. EXISTS

- Toán tử EXISTS được sử dụng để kiểm tra sự tồn tại của bất kỳ bản ghi nào trong một truy vấn con.
- Toán tử EXISTS trả về true nếu truy vấn con trả về một hoặc nhiều bản ghi.

```sql
SELECT Tên cột(s)
FROM Bảng
WHERE EXISTS
(SELECT Tên cột FROM Bảng WHERE Điều Kiện);
-- còn nhiều thể loại khác nữa nhưng tóm lại nó để kiểm tra sự tồn tại
```

12. ANY
    Toán tử ANY trả về true nếu bất kỳ giá trị truy vấn con nào đáp ứng điều kiện.

```sql
SELECT Tên cột(s)
FROM Bảng
WHERE Tên cột operator ANY
(SELECT Tên cột FROM Bảng WHERE Tên cột );
```

13. ALL

- Toán tử ALL trả về true nếu tất cả các giá trị truy vấn con đáp ứng điều kiện.

```sql
SELECT Tên cột(s)
FROM Bảng
WHERE Tên cột operator all
(SELECT Tên cột FROM table_name WHERE Điều kiện);
```

14. Operator

- toán tử so sánh chuẩn bao gồm có :

```sql
-- =, <>, !=, >, >=, <, or <=

```

15. Isnull

- khi truy vấn sql sẻ trả ra giá trị null cho các ô không có giá trị để thay đổi nó về mặc định ta sử dụng isnull (mysql là ifnull)

```sql
ISNULL(Cột , Giá trị mặc định)
```

16. ASCII

- Trả lại giá trị ASCII của ký tự đầu tiên trong

```sql
SELECT ASCII(AnhNam) AS AnhNam
FROM Nam;
-- chữ a sẽ là 65 trong ascii
```

17. CHAR

- Trả lại ký tự dựa trên mã số ASCII:

```sql
SELECT CHAR( mã số ASCII) AS MaSoCuaBan ;
```

18. CHARINDEX

- Trả về vị trí kỹ tự đầu tiên xuất hiện trong chuỗi(bắt đầu từ 1)

```sql
SELECT CHARINDEX('n', 'HainamDepTraiwwowwwowowoww') AS ViTriTimThay;
```

19. CONCAT

- Add two strings together

```sql
SELECT CONCAT('Shop', '.vn');
```

20. CONCAT_WS

- dùng để nối nhiều chuỗi với nhau phân cách bởi ký tự đầu tiên

```sql
SELECT CONCAT_WS('Ký tự nối', 'Chuỗi 1', 'chuỗi 2', 'chuỗi 3');
```

21. DATALENGTH

- trả về độ dài của Biểu thức

```sql
SELECT DATALENGTH('Hainamdeptrai.com.vn');
```

22. FORMAT

- FORMAT(Giá trị, Kiểu định dạng, vùng miền)
- Zero format điịnh dạng chúng về dạng được yêu cầu
- với date định dạng ngày tháng theo yeu cầu

```sql
--Zero
SELECT FORMAT(123456789, '00000000000');
SELECT FORMAT(123456789, '00-000-00000');
SELECT FORMAT(123456789, '###########');
SELECT FORMAT(123456789, '##-##-#####');
--date
SELECT FORMAT(CAST('2019-02-01' as date), 'MM dd yyyy');
SELECT FORMAT(Getdate(), 'D');
SELECT FORMAT(Getdate(), 'dd/MM/yyyy (MMM)');
SELECT FORMAT(Getdate(), 'YYYY-MM-DD');
SELECT FORMAT(Getdate(), 'YYYY-MM-DD HH:MI:SS');
```

- sẽ cập nhật thêm

23. LEFT

- sẽ lấy N ký tự từ trái qua và hiển thị lên

```sql
SELECT LEFT(N'Trần Hải Nam', 4) AS Ho_Cua_Toi;
```

24. LEN

- lấy ra độ dài của string

```sql
SELECT LEN('Trần Hải Nam');
```

25. LOWER()

- chuyển tất cả thành chữ thường

```sql
SELECT LOWER('Hai Nam Dep Trai wow Wow !!');
```

26. LTRIM

- loại bỏ khoảng trắng đầu đuôi

```sql
SELECT LOWER('                    Hai Nam Dep Trai wow Wow !!   ');
```

27. REPLACE

- chuyển 1 ký tự trong chuỗi thành 1 ký tự mới

```sql
SELECT REPLACE('Tran Hai Nam', 'T', 'M');
```

28. Cast

- chuyển 1 kiểu dữ liệu thành một dữ liệu khác

```sql
SELECT CAST('1999-15-07' AS varchar );
```

29. CONVERT

- chuyển 1 kiểu dữ liệu thành một dữ liệu khác
- CONVERT(data_type(length), expression, style)

```sql
SELECT CONVERT(int, 25.65);
```

30. CURRENT_USER

- trả về tên người dùng hiện tại trong csdl

```sql
SELECT CURRENT_USER;
```

31. IIF

- trả ra kết quả dựa trên điều kiện , mặc định true false

```sql
SELECT IIF(500<1000, 'YES', 'NO');
```

32. ISNUMERIC

- kiểm tra xem có phải số không

```sql
SELECT ISNUMERIC(4567);
```

-- còn rất rất nhiều nữa sẽ cập nhật sau
