# TÀI LIỆU HƯỚNG DẪN LẬP TRÌNH TỐI ƯU

Đây là phần chuyển qua MD để cho dễ đọc hơn.

## TRUY VẤN CSDL

I. Nội dung:

1. Mục đích:

 Đưa ra các yêu cầu về cách lập trình SQL để tối ưu cấu trúc cơ sở dữ liệu.

2. Các Yêu cầu:

* Sử dụng index, partition cho bảng có dữ liệu lớn

1. Với bảng có dữ liệu lớn phải đánh partition (khuyến cáo từ 2G trở lên):

* Với dữ liệu lịch sử thì đánh theo By Range;
* Với dữ liệu xác định trước được giá trị thì đánh theo By list;
* Với dữ liệu không có quy luật thì đánh theo By Hash.

2. Yêu cầu về đánh indexing:
* Đánh giá trong câu lệnh select có trường nào xác định được đối tượng tìm kiếm chính xác nhất và có độ dài trường ngắn nhất (ưu tiên trường number) thì đánh index theo trường đó
* Hạn chế đánh index theo kiểu bitmap
* Hạn chế số trường trong 1 index.
* Với các bảng có đánh partition thì index phải đánh theo local

3. Khuyến cáo khi khởi tạo các bảng có dữ liệu lớn:
* Hạn chế dùng foreign key
* Hạn chế sử dụng trigger trên bảng
* Với các bảng có tần suất update hoặc insert lớn không nên dùng primary key (Áp dụng bắt buộc chỉ trừ những trường hợp đặc biệt không xử lý được từ code hoặc nếu xử lý được thì chi phí rất cao)
* Tối ưu câu lệnh truy vấn và tác động vào các bảng đã đánh partition, indexing

4. Tất cả các câu lệnh đều phải có index, không câu lệnh nào được quét full bảng

5. Nếu bảng có partition thì trong điều kiện câu lệnh phải có thêm trường partition, ngoại trừ 1 số trường hợp đặc biệt

6. Khi join 2 bảng với nhau thì bảng có dữ liệu lớn hơn phải có index

7. Trong câu lệnh không dùng điều kiện is null, phải chuyển sang phương án dùng các toán tử : >, < = ….

8. Với các bảng tmp có dữ liệu trong quá trình chạy và xóa dữ liệu sau khi chạy (không cần backup dữ liệu) :

* Tạo bảng ở chế độ Nologging
* Khi insert phải dùng /*+Append*/
* Nếu muốn xóa cả bảng hoặc 1 partition của bảng phải dùng câu lệnh truncate.
* Hạn chế sử dụng câu lệnh update, cần tối ưu câu lệnh insert và select
* Yêu cầu trong các câu lệnh tạo View:

9. Trong view không thêm trường ’ảo’ của Database vì khi câu lệnh select vào view có thể sẽ bị quét full bảng.

10.Hạn chế sử dụng view lồng nhau, tối đa chỉ dùng 2 view lồng nhau

11.Nếu cần hint index trong câu lệnh truy vấn vào view thì cần hint trong câu lệnh tạo view, không hint vào trong câu lệnh select vào view

* Yêu cầu tối ưu câu lệnh truy vấn vào Database

12. Yêu cầu tối ưu lệnh select:

* Không thực hiện select * dữ liệu trong bảng, phải chỉ rõ các trường cần select
* Chỉ thực hiện select số num row cần sử dụng (càng ít num row hiệu suất truy vấn dữ liệu càng nhanh)

13.Giảm thiểu số lượng Subqueries trong truy vấn

14. Sử dụng IN và EXISTS một cách thích hợp trong câu lệnh truy vấn

15. Sử dụng EXISTS và DISTINCT khi join các bảng có quan hệ 1 nhiều

16. Thay thế UNION ALL cho UNION

17. Yêu cầu với câu lệnh WHERE

* Điều kiện where khi dùng is not phải chuyển sang dùng các toán tử : >, < =
* Điều kiện where khi dùng điều kiện kép lớn hơn hoặc nhỏ hơn trong khoảng, phải chuyển sang sử dụng BETWEEN

18. Sử dụng JOIN thay cho Subqueries để tăng hiệu suất truy vấn

19.Không sử dụng toán tử OR trong câu lệnh truy vấn bảng có dữ liệu lớn

20.Đánh index cho foreign key trên bảng con

PHỤ LỤC: CÁCH THỰC HIỆN

* Cách thực hiện

1. Sử dụng index, partition cho bảng có dữ liệu lớn
	1.1. Với bảng có dữ liệu lớn (2G trở lên) phải đánh partition:
	
	* Thông thường, với các bảng có dữ liệu lớn > 1 triệu bản ghi hoặc các bảng có dữ liệu > 2G phải thực hiện đánh partition theo ngày, tháng, năm tùy theo mức độ tăng trưởng của dữ liệu. Các bảng dữ liệu lớn nếu các truy vấn cho ứng dụng hoặc báo cáo điều kiện tìm kiếm theo ngày thì đánh Partition theo ngày, theo tháng thì đánh Partition
theo tháng, theo năm thì đánh Partition theo năm.

	* Cách đánh parititon:
		- Range Partitioning: Sử dụng cho các dữ liệu có định dạng ngày tháng, part number hoặc serial number
		- List Partitioning: Được sử dụng cho các dữ liệu không có sự liên quan đến nhau:
			Partition theo các quốc gia trong cùng 1 khu vực, hoặc theo các chữ cái vần A, B, C, D …
		- Hash Partitioning: Được sử dụng khi không sử dụng được theo Range Partition và List Partition
		
	1.2. Yêu cầu về đánh indexing
	
	* Đánh giá trong câu lệnh select có trường nào xác định được đối tượng tìm kiếm chính xác nhất và có độ dài trường ngắn nhất (ưu tiên trường number) thì đánh index theo trường đó.
	* Ví dụ: cách xác định trường thông tin đánh indexing: Bảng sale_trans có 2 trường là username varchar2(10) và user_id number(5), trong trường hợp này phải đánh index và tìm kiếm theo user_id

	1.3. Khuyến cáo khi khởi tạo các bảng có dữ liệu lớn
	
	* Hạn chế xử lý nghiệp vụ dưới tầng Database như triger, FK  Làm tăng tải Database, khó có thể mở rộng database theo chiều ngang, nếu xử lý nghiệp vụ ở lớp APP thì có thể tăng thêm tài nguyên cho APP
	* Khi DB cao tải có thể gây lỗi và downtime cho dịch vụ, nếu cao tải ở lớp APP thì có thể retart APP và chỉ ảnh hưởng 1 phần khách hàng trong 1 thời gian ngắn. Nếu dùng FK, thì trường này phải được đánh index

2. Tối ưu câu lệnh truy vấn và tác động vào các bảng đã đánh partition, indexing
	2.1. Các câu lệnh đều phải quét bảng theo index, không được quét full bảng
		* Tất cả các câu lệnh đều phải có index, không câu lệnh nào được quét full bảng.
		* Ví dụ: câu lệnh đều phải có index, không câu lệnh nào được quét full bảng. Bảng sale_trans_detail có 3 trường : sale_trans_id, username, user_id và đánh index theo user_id
		* Câu lệnh tối ưu : phải đánh index theo sale_trans_id theo trường kiểm tra điều kiện là ’sale_trans_id=:1’ Select sale_trans_id, username, user_id from sale_trans_detail where sale_trans_id=:1

Câu lệnh không tối ưu:

```
Select sale_trans_id, username, user_id from sale_trans_detail
where sale_trans_id=:1
```

2.2. Nếu bảng có partition thì trong câu lệnh phải có thêm trường partition, ngoại trừ 1 số trường hợp đặc biệt

* Câu lệnh phải có thêm trường partition nếu bảng được đánh partition:

Ví dụ: bảng sale_trans_detail có 4 trường: create_date,sale_trans_id, username, user_id . Đánh index theo sale_trans_id và partition theo create_date

* Câu lệnh tối ưu: bổ sung điều kiện ràng buộc cho trường được partition ‘ create_date>=:2’
```
Select sale_trans_id, username, user_id 
from sale_trans_detail
where create_date>=:2 and sale_trans_id=:1
```
* Câu lệnh không tối ưu:

```
Select sale_trans_id, username, user_id 
from sale_trans_detail
where sale_trans_id=:1
```

2.3. Khi join 2 bảng với nhau thì bảng có dữ liệu lớn hơn phải có index

* Ví dụ: Có 2 bảng là staff và sale_trans. Bảng staff chứa thông tin nhân viên, bảng sale_trans thống kê các giao dịch bán hàng trên hệ thống. Dữ liệu của bảng sale_trans lớn
hơn so với bảng staff.
 
Câu lệnh tối ưu: đánh index cho bảng sale_trans có dữ liệu lớn hơn theo trường user_id

```
Select user_id 
from sale_trans a, staff b 
where b.user_id=a.user_id and b.user_id=:1
```
* Câu lệnh không tối ưu:
```
Select user_id 
from sale_trans a, staff b 
where a.user_id=b.user_id and b.user_id=:1
```

2.4.Trong câu lệnh không dùng điều kiện is null, phải chuyển sang phương án dùng các toán tử : >, < = ….

Ví dụ: bảng sale_trans có trường user_id có thể là null, có đánh index theo user_id
* Câu lệnh không tối ưu: sửa lại cấu trúc bảng, đặt default cho trường user_id là 0 (tùy chọn)

```
Select user_id 
from sale_trans user_id = 0
```
* Câu lệnh không tối ưu:

```
Select user_id from sale_trans user_id is null
```

2.5. Với các bảng tmp có dữ liệu trong quá trình chạy và xóa dữ liệu sau khi chạy (không cần backup dữ liệu) cần chuyển bảng sang nologging và câu lệnh insert cần có thêm append:

Ví dụ: trong 1 thủ tục cần sinh ra bảng proces_temp

* Câu lệnh tối ưu:
```
Create table process_temp(f varchar2(10));
Insert into process_temp(f) values(’1’);
Delete process_temp;
```
* Câu lệnh không tối ưu:
```
Create table process_temp(f varchar2(10)) nologging;
Insert /*APPEND*/ into process_temp(f) values(’1’);
Truncate table process_temp;
```
3. Yêu cầu trong các câu lệnh tạo View:

3.1.Trong view không nên thêm trường ảo vì khi câu lệnh select vào view có thể sẽ bị quét full bảng

* Ví dụ: có 2 bảng table 1, table 2 được đánh index theo f1 hoặc f2, rowid là một trường ảo.
* Câu lệnh tối ưu: khi trong view chỉ lấy trường thực của bảng cần lấy f1, f2 của table 1, table 2.
```
Create view baocao as (select f1,f2 from table1, table2 where table1.id=table2.id )
```
* Câu lệnh không tối ưu: khi lấy thêm trường ảo rowid thì có thể không nhận index f1, f2 đã đánh, khi đó câu lệnh dưới sẽ quét full bảng.

```
Create view baocao as (select rowid, f1, f2 from table1, table2 where table1.id=table2.id)
```
3.2. Hạn chế sử dụng view lồng nhau
* Câu lệnh tối ưu: câu lệnh dưới view baocao được gọi từ 2 bảng table 1, table 2,không sử dụng view lồng nhau.
```
Create view baocao as (select f1,f2 from table1, table2 where table1.id=table2.id)
```
* Câu lệnh không tối ưu: câu lệnh ở dưới sử dụng view lồng 3 lớp, view baocao2 được gọi từ 2 bảng table 3, table 4; view baocao1 được gọi từ baocao2
và table 2; view baocao được gọi từ baocao1 và table 1.

```
Create view baocao as (select f1,f2 from baocao1, table1 where baocao1.id=table1.id);
Create view baocao1 as (select f1,f2 from baocao2, table2 where table2.id=baocao2.id)
Create view baocao2 as (select f1,f2 from table3, table4 where table4.id=table3.id)
```

3.3. Nếu cần hint index trong câu lệnh truy vấn vào view thì cần hint trong câu lệnh tạo view, không hint vào trong câu lệnh select vào view

* Câu lệnh tối ưu: sử dụng hint index /*+INDEX(table1 index1)*/ trong câu lệnh tạo view baocao. Hint này chỉ rõ table 1 sử dụng index1.
```
Create view baocao as (select /*+INDEX(table1 index1)*/ f1,f2
from table1, table2 where table1.id=table2.id)
```
* Câu lệnh không tối ưu: sử dụng hint index /*+INDEX(table1 index1)*/ trong câu lệnh select ngoài gọi vào view baocao. Khi đó với hint này không hiểu
index1 được sử dụng cho table nào.
```
select /*+INDEX(table1 index1)*/ f1,f2 from baocao
```
4. Yêu cầu tối ưu câu lệnh truy vấn vào Database

4.1.Tối ưu câu lệnh select:

* Không thực hiện select * dữ liệu trong bảng mà phải chỉ rõ các trường cần select
* Câu lệnh tối ưu:
```
SELECT id, first_name, last_name, age, subject FROM
student_details;
```
* Câu lệnh không tối ưu:
```
SELECT * FROM student_details;
```
4.2. Giảm thiểu số lượng Subqueries trong truy vấn

* Câu lệnh tối ưu:
```
SELECT name FROM employee
WHERE (salary, age ) = (SELECT MAX (salary), MAX (age)
FROM employee_details)
AND dept = 'Electronics';
```
* Câu lệnh không tối ưu:
```
SELECT name FROM employee
WHERE salary = (SELECT MAX(salary) 
FROM employee_details)
AND age = (SELECT MAX(age) 
 	   FROM employee_details)
AND emp_dept = 'Electronics';
```

4.3. Sử dụng IN và EXISTS một cách thích hợp trong câu lệnh truy vấn

* Thông thường IN sẽ có hiệu năng thấp nhất, nên sử dụng IN ở sub-query, sử dụng EXISTS ở main-query
* Câu lệnh tối ưu:
```
Select * from product p
where EXISTS (select * from order_items o
where o.product_id = p.product_id)
```
* Câu lệnh không tối ưu:
```
Select * from product p
where product_id IN (select product_id from order_items)
```

4.4. Sử dụng EXISTS thay vì dùng DISTINCT khi join các bảng có quan hệ 1 nhiều:

* Sử dụng EXISTS thay vì dùng DISTINCT
* Câu lệnh tối ưu:
```
SELECT d.dept_id, d.dept FROM dept d
WHERE EXISTS ( SELECT 'X' FROM employee e WHERE e.dept = d.dept);
```
* Câu lệnh không tối ưu:
```
SELECT DISTINCT d.dept_id, d.dept
FROM dept d,employee e
WHERE e.dept = e.dept;
```
4.5. Thay thế UNION ALL cho UNION:

* Câu lệnh tối ưu:
```
SELECT id, first_name
FROM student_details_class10
UNION ALL
SELECT id, first_name
FROM sports_team;
```
* Câu lệnh không tối ưu:
```
SELECT id, first_name, subject
FROM student_details_class10
UNION
SELECT id, first_name
FROM sports_team;
```
4.6. Yêu cầu với câu lệnh WHERE:

* Điều kiện where khi dùng is not, phải chuyển sang phương án dùng các toán tử : >, < =

* Câu lệnh tối ưu:
```
SELECT id, first_name, age
FROM student_details
WHERE age > 10;
```
* Câu lệnh không tối ưu:
```
SELECT id, first_name, age
FROM student_details
WHERE age != 10;
Hoặc:
SELECT id, first_name, age 
FROM student_details
WHERE age NOT = 10;
```
* Điều kiện where khi dùng điều kiện kép lớn hơn hoặc nhỏ hơn trong khoảng, phải chuyển sang sử dụng BETWEEN
* Câu lệnh tối ưu:
```
SELECT product_id, product_name
FROM product
WHERE unit_price BETWEEN MAX(unit_price) and
MIN(unit_price)
```
* Câu lệnh không tối ưu:
```
SELECT product_id, product_name
FROM product
WHERE unit_price >= MAX(unit_price)
and unit_price <= MIN(unit_price)
```
4.7. Sử dụng JOIN thay cho Subqueries để tăng hiệu suất câu lệnh truy vấn:

* Sử dụng JOIN thay cho Subqueries
* Câu lệnh tối ưu:
```
SELECT a.id, MAX(p.created) AS latest_post
FROM authors a
INNER JOIN posts p ON (a.id = p.author_id)
GROUP BY a.id
```
* Câu lệnh không tối ưu:
```
SELECT a.id,
	(SELECT MAX(created)
	FROM posts
	WHERE author_id = a.id) AS latest_post 
FROM authors a
```

4.8. Tránh sử dụng toán tử OR trong câu lệnh truy vấn bảng có dữ liệu lớn Bảng dữ liệu lớn: bảng có dữ liệu lớn > 1 triệu hoặc các bảng có dữ liệu lớn > 1 GB

4.9. Đánh index cho foreign key trên bảng con

* Ví dụ: cho 2 bảng supplier (bảng cha) và product (bảng con). Trường supplier_id là foreign key của bảng product.
```
CREATE TABLE supplier 
( 
supplier_id number(10) not null,
supplier_name varchar2(50) not null,
contact_name varchar2(50),
CONSTRAINT supplier_pk PRIMARY KEY (supplier_id)
);

INSERT INTO supplier VALUES (1, 'Supplier 1', 'Contact 1');
INSERT INTO supplier VALUES (2, 'Supplier 2', 'Contact 2');
COMMIT;

CREATE TABLE product
(
product_id number(10) not null,
product_name varchar2(50) not null,
supplier_id number(10) not null,
CONSTRAINT fk_supplier
FOREIGN KEY (supplier_id)
REFERENCES supplier(supplier_id)
ON DELETE CASCADE 
);

INSERT INTO product VALUES (1, 'Product 1', 1);
INSERT INTO product VALUES (2, 'Product 2', 1);
INSERT INTO product VALUES (3, 'Product 3', 2);

COMMIT;
```
* Câu lệnh tối ưu: Thêm index cho foreign key trên bảng Product bằng câu lệnh phía dưới. Khi thực hiện các câu lệnh truy vấn vào bảng supplier (ví dụ:
```
DELETE supplier WHERE supplier_id = 1; INSERT INTO
supplier VALUES (5, 'Supplier 5', 'Contact 5');) 
```
đều hoạt động tốt, do Oracle loại bỏ tất cả các locks xảy ra ở bảng con product.
```
CREATE INDEX fk_supplier ON product (supplier_id);
```
* Câu lệnh không tối ưu: không đánh index cho foreign key (supplier_id) trên bảng product. Khi thực hiện các lệnh truy vấn vào bảng supplier xảy ra hiện trượng treo nghẽn, hiện ra thông báo "enq: TM - contention". 

Tham khảo
1. http://docs.oracle.com/cd/B28359_01/server.111/b32024/partition.htm
2. http://www.confio.com/logicalread/solving-oracle-enq-tm-contention-waitevents/#.UhrHiNKnoeY