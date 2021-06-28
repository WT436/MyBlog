# Cơ bản về SQL Server

## Câu lệnh : INSERT

Câu lệnh INSERT INTO được sử dụng để chèn các bản ghi mới trong bảng.

cái này là muốn cột nào thì thêm vào cột đó

```sql
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```

còn cái này thì phải thêm theo thứ tự code , lệch nhát là cụ đi chân lạnh toát ngay

```sql
INSERT INTO table_name
VALUES (value1, value2, value3, ...);
```

## Câu lệnh : SELECT

- Câu lệnh SQL SELECT Câu lệnh SELECT được sử dụng để chọn dữ liệu từ cơ sở dữ liệu.
- Dữ liệu trả về được lưu trữ trong một bảng kết quả, được gọi là tập kết quả.

1. cú pháp

```sql
SELECT cột 1, cột 2, ...
FROM tên bảng;
```

2. Muốn lấy tất cả dữ liệu của bảng mục tiêu thì dùng cú pháp

```sql
SELECT * FROM tên bảng;
```

-  câu lệnh này còn được kết hợp với rất nhiều các từ khóa câu lệnh đi sau

4. SELECT DISTINCT

câu lệnh này dùng để loại bỏ những record có giá trị giống nhau ra

```sql
SELECT DISTINCT Country FROM Customers;
-- như vậy thì các Country trong bảng Customers khi được select ra thì nó chỉ có một giá trị duy nhất mà thôi
```

5. ALL

Tùy chọn, trả lại tất cả các hàng phù hợp. câu lệnh này ngược hoàn toàn vs DISTINCT , nó sẽ lấy tất tần tật , tuốt tuồn tuột mọi thứ ra , như cách mà tào tháo làm vs chúng ta

```sql
SELECT ALL Country FROM Customers;
```

6. TOP
   
Tùy chọn. Nếu chỉ định cụ thể sẽ trả về những giá trị đầu trong bộ kết quả dựa trên giá trị đã chon. tức là bạn muốn lấy 10 20 30 .... các giá trị đầu tiên trong phần tìm kiếm , ok là nó đấy

```sql
select top(20)* from Tinh
```

7. PERCENT

là số phần trăm trả ra từ câu select mk dùng nó vs top

```sql
select top(10) PERCENT * from Customers;
```

8. WITH TIES
   
tương tự như top nó cx sẽ lấy ra vd chọn 10 ra 10 , nhưng nếu như trong 10 Customers của bạn có cùng tuổi chẳng hạn cái này nó sẽ lấy tất tần tật tuốt tuồn tuột ra (nó phải có order by cái này phần sau)

```sql
select top(10) * from Huyen
```

> kết quả

```console
964	Thành phố Cà Mau	96
966	Huyện U Minh	96
967	Huyện Thới Bình	96
968	Huyện Trần Văn Thời	96
969	Huyện Cái Nước	96
970	Huyện Đầm Dơi	96
971	Huyện Năm Căn	96
972	Huyện Phú Tân	96
973	Huyện Ngọc Hiển	96
954	Thành phố Bạc Liêu	95
```

với WITH TIES

```sql
select top(10) WITH TIES * from Huyen order by IDTP desc
```

> kết quả

```console
964	Thành phố Cà Mau	96
966	Huyện U Minh	96
967	Huyện Thới Bình	96
968	Huyện Trần Văn Thời	96
969	Huyện Cái Nước	96
970	Huyện Đầm Dơi	96
971	Huyện Năm Căn	96
972	Huyện Phú Tân	96
973	Huyện Ngọc Hiển	96
954	Thành phố Bạc Liêu	95
956	Huyện Hồng Dân	95
957	Huyện Phước Long	95
958	Huyện Vĩnh Lợi	95
959	Thị xã Giá Rai	95
960	Huyện Đông Hải	95
961	Huyện Hoà Bình	95
```

9. as
   
 là lệnh đổi tên cột khi đươc trả ra

```sql
select top(10) NameQH as N'Tên Quận Huyện' from Huyen
```

kết quả

```console
Tên Quận Huyện
-------------------
Quận Ba Đình
Quận Hoàn Kiếm
Quận Tây Hồ
Quận Long Biên
Quận Cầu Giấy
Quận Đống Đa
Quận Hai Bà Trưng
Quận Hoàng Mai
Quận Thanh Xuân
Huyện Sóc Sơn
```
## Câu lệnh :  UPDATE

Câu lệnh UPDATE được sử dụng để sửa đổi các bản ghi hiện có trong bảng.

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
- nhớ kỹ là phải có where

## Câu lệnh :  DELETE

Câu lệnh DELETE được sử dụng để xóa các bản ghi hiện có trong bảng.

```sql
DELETE FROM table_name WHERE condition;
```

Thao tác này sẽ xóa tất cả dữ liệu khỏi bảng. Bảng sẽ không chứa hàng sau khi bạn chạy mã này. Không giống như DROP TABLE, điều này bảo toàn bảng và cấu trúc của nó và bạn có thể tiếp tục chèn các hàng mới vào bảng đó.

Ngoài ra còn có : TRUNCATE
```
TRUNCATE TABLE HelloWords
```

- Sự khác biệt với thao tác DELETE là một số:

1. Không thể TRUNCATE một bảng nếu có tham chiếu FOREIGN KEY.
2. Nếu bảng tham gia vào một INDEXED VIEW.
3. Nếu bảng được xuất bản bằng cách sử dụng TRANSACTIONAL REPLICATION hoặc MERGE REPLICATION.
4. Nó sẽ không kích hoạt bất kỳ TRIGGER nào được xác định trong bảng.

## Câu lệnh : Joins

Joins rất hữu ích khi chúng ta phải truy xuất dữ liệu trên nhiều bảng có mối liên hệ với nhau.

Nó gồm các dạng như sau : (Ở đây chúng ta sẽ sử dụng bộ csdl địa chỉ của việt nam để làm phần demo:)

- (INNER) JOIN: Trả về các bản ghi có giá trị phù hợp trong cả hai bảng.

![image](https://user-images.githubusercontent.com/63473793/123607745-5b7ad480-d828-11eb-9a88-4099b4e5b0c1.png)

- syntax

```
SELECT * 
FROM [Tinh]
INNER JOIN [Huyen] ON Tinh.IDTP = Huyen.IDTP

OR

SELECT * 
FROM [Tinh]
JOIN [Huyen] ON Tinh.IDTP = Huyen.IDTP
```
Kết quả Nhận được :

```
1	Thành phố Hà Nội	268	Quận Hà Đông	1
1	Thành phố Hà Nội	269	Thị xã Sơn Tây	1
1	Thành phố Hà Nội	271	Huyện Ba Vì	1
1	Thành phố Hà Nội	272	Huyện Phúc Thọ	1
1	Thành phố Hà Nội	273	Huyện Đan Phượng	1
1	Thành phố Hà Nội	274	Huyện Hoài Đức	1
1	Thành phố Hà Nội	275	Huyện Quốc Oai	1
1	Thành phố Hà Nội	276	Huyện Thạch Thất	1
1	Thành phố Hà Nội	277	Huyện Chương Mỹ	1
1	Thành phố Hà Nội	278	Huyện Thanh Oai	1
1	Thành phố Hà Nội	279	Huyện Thường Tín	1
-- nó rất dài vì lấy tất cả ra nên ở đây chúng ta sẽ cắt ngắn phần  dữ liệu này hoặc có thể dùng TOP ...
```
- Tương tự với các kiểu JOIN khác được mô ta như ở bên dưới : 

- LEFT (OUTER) JOIN: Trả về tất cả các bản ghi từ bảng bên trái và các bản ghi đã so khớp từ bảng bên phải.

![image](https://user-images.githubusercontent.com/63473793/123607760-603f8880-d828-11eb-8a76-a8faaa82ca60.png)

- RIGHT (OUTER) JOIN: Trả về tất cả các bản ghi từ bảng bên phải và các bản ghi phù hợp từ bảng bên trái.

![image](https://user-images.githubusercontent.com/63473793/123607783-646ba600-d828-11eb-838e-3f1a7bc89c53.png)

- FULL (OUTER) JOIN: Trả về tất cả các bản ghi khi có một kết quả phù hợp trong bảng bên trái hoặc bên phải.

![image](https://user-images.githubusercontent.com/63473793/123607801-6897c380-d828-11eb-951f-909c3e2f9144.png)

## Table Aliases

VÍ dụ như chúng ta có một tên bảng dài hoặc là có rất nhiều bảng mà chúng có thể gây rối trong lúc sử lý. Lúc này Table Aliases có vai trò định vị cũng như gỡ rối bằng cách đặt tên logic cho phần bảng chúng ta muốn truy xuất

- Syntax
 
``` 
<TableName> [as] <alias>
```

Ví Dụ : 
```
SELECT [Tinh].IDTP as 'ID_Thanh_Pho' , [Huyen].IDQH as 'ID_Quan_Huyen'
FROM [Tinh]
JOIN [Huyen] ON Tinh.IDTP = Huyen.IDTP
```

## Câu lệnh : Unions

Như chúng ta thấy một JOINS sẽ kết hợp các columns  lại với nhau vậy các rows thì sao . chúng ta đã có UNION

```
SELECT column_name(s) FROM table1
UNION 
SELECT column_name(s) FROM table2;

-- nếu như muốn lấy cả các giá trị trùng nhau thì dùng

SELECT column_name(s) FROM table1
UNION ALL
SELECT column_name(s) FROM table2;
```
Ví Dụ : 

```
SELECT [Tinh].NameTP FROM [Tinh]
UNION ALL
SELECT [Huyen].NameQH FROM [Huyen];
```

## Table Variables

Nó có thể hữu ích, nếu bạn cần xử lý dữ liệu tạm thời (đặc biệt là trong một thủ tục được lưu trữ), sử dụng các biến bảng: Sự khác biệt giữa bảng "thực" và một biến bảng là nó chỉ tồn tại trong bộ nhớ để xử lý tạm thời.

```sql
DECLARE @Region TABLE
(
 RegionID int,
 RegionDescription NChar(50)
)
```

## PRINT

Hiển thị thông báo đến bảng điều khiển đầu ra. Sử dụng SQL Server Management Studio, điều này sẽ được hiển thị trong tab thông báo, thay vì tab kết quả:

```
PRINT 'Hello World!';
```

Thật ra thì Tôi cũng chả bao giò dùng đến cái này :D

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>

