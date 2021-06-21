# Stored Procedure

## định Nghĩa

- Procedure (Thủ tục) là một chương trình trong cơ sở dữ liệu gồm nhiều câu lệnh mà bạn lưu lại cho những lần sử dụng sau. Trong SQL Server, bạn có thể truyền các tham số vào procedure, tuy nó không trả về một giá trị cụ thể như function (hàm) nhưng cho biết việc thực thi thành công hay thất bại.

cú pháp :

```console
CREATE { PROCEDURE | PROC } [schema_name.]procedure_name
 [ @parameter [type_schema_name.] datatype
 [ VARYING ] [ = default ] [ OUT | OUTPUT | READONLY ]
 , @parameter [type_schema_name.] datatype
 [ VARYING ] [ = default ] [ OUT | OUTPUT | READONLY ] ]

 [ WITH { ENCRYPTION | RECOMPILE | EXECUTE AS Clause } ]
 [ FOR REPLICATION ]

 AS

 BEGIN
 [declaration_section]

 executable_section

 END;
```

- schema_name: Tên schema (lược đồ) sở hữu procedure.
- procedure_name: Tên gán cho procedure
- @parameter: Một hay nhiều tham số được truyền vào hàm.
- type_schema_name: Kiểu dữ liệu của schema (nếu có).
- Datatype: Kiểu dữ liệu cho @parameter.
- Default: Giá trị mặc định gán cho @parameter.
- OUT/OUTPUT: @parameter là một tham số đầu ra
- READONLY: @parameter không thể bị procedure ghi đè lên.
- ENCRYPTION: Mã nguồn (source) của procedure sẽ không được lưu trữ dưới dạng text trong hệ thống.
- RECOMPILE: Truy vấn sẽ không được lưu ở bộ nhớ đệm (cache) cho thủ tục này.
- EXECUTE AS clause: Xác định ngữ cảnh bảo mật để thực thi thủ tục.
- FOR REPLICATION: Procedure đã lưu sẽ chỉ được thực thi trong quá trình replication (nhân bản).

vd1 :

```sql
CREATE PROCEDURE spNhanvien
 @nhanvien_name VARCHAR(50) OUT

 AS
 BEGIN
 DECLARE @nhanvien_id INT;
 SET @nhanvien_id = 8;
 IF @nhanvien_id < 10
 SET @nhanvien_name = 'Smith';
 ELSE
 SET @nhanvien_name = 'Lawrence';

 END;
```

- Thủ tục trên được gán tên là spNhanvien, có một tham số là @nhanvien_name, output của tham số sẽ được dựa trên @nhanvien_id.

- Sau đó, bạn có thể thực hiện tham chiếu spNhanvien như sau:

```sql
USE [test]
 GO

 DECLARE @site_name varchar(50);
 EXEC FindSite @site_name OUT;
 PRINT @site_name;

 GO
```

## Drop Procedure (Xóa bỏ Procedure)

- Một khi đã tạo thành công các procedure thì cũng sẽ có những trường hợp bạn muốn xóa bỏ procedure khỏi cơ sở dữ liệu vì một vài lý do.

- Cú pháp
  Để xóa bỏ một procedure, ta có cú pháp sau:

- DROP PROCEDURE procedure_name;
- Tham số: procedure_name: Tên procedure bạn muốn xóa bỏ...

- Ví dụ :DROP PROCEDURE spNhanvien;

## Biến trong thủ tục lưu trữ

- các biến trong thủ tục được khai báo Declanre theo cấu trúc

```sql
declare @Bien int
```

## tham số output

- để có được tham số output trả ra thì ta làm theo cú pháp

```sql
@ten_Tham_so output
```

## lệnh return

- như output , return trả về giá trị cho đối tượng thực thi proc

```sql
create proc Sp_TestReturn
as
begin
declare @out int
      select @out = count(*) from Test
      return @out
end
-- thục thi
declare @a int
exec @a = Sp_TestReturn
select @a
```

- nguồn : https://quantrimang.com/procedure-thu-tuc-trong-sql-server-159768
