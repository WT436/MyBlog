# Điều kiện ( Where ) Sql

Mệnh đề WHERE có thể được kết hợp với các toán tử AND, OR và NOT. <br>
Toán tử AND và OR được sử dụng để lọc các bản ghi dựa trên nhiều hơn một điều kiện: <br>
Toán tử AND hiển thị một bản ghi nếu tất cả các điều kiện được phân tách bằng AND đều ĐÚNG.<br>
Toán tử OR hiển thị một bản ghi nếu bất kỳ điều kiện nào được phân tách bởi OR là TRUE.<br>

## Cú pháp

1. AND

- kết hợp cả 2 điều kiện chính xác

```sql
SELECT cột_1, cột_2, ...
FROM Bảng
WHERE Điều_Kiện_1 AND Điều_Kiện_2 AND Điều_Kiện_3 ...;
```

2. OR
   chỉ cần 1 điều kiện chính xác

```sql
SELECT cột_1, cột_2, ...
FROM Bảng
WHERE Điều_Kiện_1 OR Điều_Kiện_2 OR Điều_Kiện_3 ...;
```

3. NOT
   nó làm ngược lại điều Kiện

```SQl
SELECT cột_1, cột_2, ...
FROM Bảng
WHERE NOT Điều_Kiện;
```
