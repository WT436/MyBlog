# Where

1. Tìm một hàng bằng cách sử dụng một đẳng thức đơn giản

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE LastName = 'Smith' ;
```

2. Tìm các hàng có chứa giá trị như một phần của chuỗi

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE LastName LIKE ('%Smi%');
```

3. Tìm hàng bằng cách sử dụng toán tử so sánh

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE EmployeeKey  <= 500;
```

4. Tìm các hàng đáp ứng bất kỳ điều kiện nào trong ba điều kiện

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE EmployeeKey = 1 OR EmployeeKey = 8 OR EmployeeKey = 12;
```

5. Tìm các hàng phải đáp ứng một số điều kiện

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE EmployeeKey <= 500 AND LastName LIKE '%Smi%' AND FirstName LIKE '%A%';
```

6. Tìm các hàng trong danh sách các giá trị

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE LastName IN ('Smith', 'Godfrey', 'Johnson');
```

7. Tìm các hàng có giá trị giữa hai giá trị

```sql
SELECT EmployeeKey, LastName
FROM DimEmployee
WHERE EmployeeKey Between 100 AND 200;
```
