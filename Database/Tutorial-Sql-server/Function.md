# Function

- là một đối tượng trong cơ sở dữ liệu bao gồm một tập nhiều câu lệnh được nhóm lại với nhau và được tạo ra với mục đích sử dụng lại. Trong SQL Server, hàm được lưu trữ và bạn có thể truyền các tham số vào cũng như trả về các giá trị.

```console
CREATE FUNCTION [schema_name.]function_name
 ( [ @parameter [ AS ] [type_schema_name.] datatype
 [ = default ] [ READONLY ]
 , @parameter [ AS ] [type_schema_name.] datatype
 [ = default ] [ READONLY ] ]
 )

 RETURNS return_datatype

 [ WITH { ENCRYPTION
 | SCHEMABINDING
 | RETURNS NULL ON NULL INPUT
 | CALLED ON NULL INPUT
 | EXECUTE AS Clause ]

 [ AS ]

 BEGIN

 [declaration_section]

 executable_section

 RETURN return_value

 END;
 Tham số:

- schema_name: Tên schema (lược đồ) sở hữu function.
- function_name: Tên gán cho function.
- @parameter: Một hay nhiều tham số được truyền vào hàm.
- type_schema_name: Kiểu dữ liệu của schema (nếu có).
- Datatype: Kiểu dữ liệu cho @parameter.
- Default: Giá trị mặc định gán cho @parameter.
- READONLY: @parameter không thể bị function ghi đè lên.
- return_datatype: Kiểu dữ liệu của giá trị trả về.
- ENCRYPTION: Mã nguồn (source) của function sẽ không được lưu trữ dưới dạng text trong hệ thống.
- SCHEMABINDING: Đảm bảo các đối tượng không bị chỉnh sửa gây ảnh hưởng đến function.
- RETURNS NULL ON NULL INPUT: Hàm sẽ trả về NULL nếu bất cứ parameter nào là NULL.
- CALL ON NULL INPUT: Hàm sẽ thực thi cho dù bao gồm tham số là NULL.
- EXECUTE AS clause: Xác định ngữ cảnh bảo mật để thực thi hàm.
- return_value: Giá trị được trả về.
```

```sql
CREATE FUNCTION fuNhanvien
 ( @nhanvien_id INT )

 RETURNS VARCHAR(50)

 AS

 BEGIN

 DECLARE @nhanvien_name VARCHAR(50);

 IF @nhanvien_id < 10
 SET @nhanvien_name = 'Smith';
 ELSE
 SET @nhanvien_name = 'Lawrence';

 RETURN @nhanvien_name;

 END;
```

### Scalar UDF Hàm Vô Hướng

- UDF được tạo câu lệnh create function có cấu trúc như sau :

```sql
create function Tên_hàm ([danh sách tham số]) returns(kiểu trả về của hàm)
as
begin
các câu lệnh của hàm
return (Biến)
-- cái này nó giống function
end
```

### Hàm Nội tuyến - inline UDF

- UDF là hàm return table

```sql
create function Tên_Hàm([Danh sách tham số])
returns table
as
return (Câu lệnh)
```

### Multi statement UDF

```sql
create function Tên_Hàm([Danh sách tham số])
returns @biến_Bảng table(danh sách biến cột)
as
begin
các câu lệnh trả vào table
return
end
```
