# union

- Mỗi câu lệnh SELECT trong UNION phải có cùng số cột
- Các cột cũng phải có kiểu dữ liệu tương tự
- Các cột trong mỗi câu lệnh SELECT cũng phải theo cùng một thứ tự
- cũng giống như join nhưng cái bnayf nó sẽ ốp 2 cột của 2 bảng lại vs nhau

## union

- lấy những giá trị của 2 cột và loại những giá trị giống nhau

```sql
(
    SELECT 1 ID
    UNION
    SELECT 2
    UNION
    SELECT 3
)
UNION
(
    SELECT 3
    UNION
    SELECT 4
    UNION
    SELECT 5
);
--kết quả trả ra là 1 2 3 4 5 // mất 1 cái 3
```

## Union All

- cx giống như union nhưng nó sẽ không loại những giá trị giống nhau ra

## INTERSECT

- chỉ lấy các giá trị mà cả 2 cột có và chỉ lấy 1 lần kết quả chỉ trả ra là 3

## EXCEPT

- lấy tất cả (trừ cả giá trị xuất hiện bên cột 2) của cột đầu và không lấy bất kể giá trị nào có bên cột 2 và giá trị cột 2 xuât hiện ở cột 1
