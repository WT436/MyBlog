# ORDER BY Và GROUP BY

## ORDER BY

1. định nghĩa

- Từ khóa ORDER BY được sử dụng để sắp xếp tập hợp kết quả theo thứ tự tăng dần hoặc giảm dần.
- Từ khóa ORDER BY sắp xếp các bản ghi theo thứ tự tăng dần theo mặc định.

2. cú pháp

```sql
SELECT cột_1, cột_2, ...
FROM Bảng
ORDER BY cột_1, cột_2, ... ASC|DESC;
```

3. có 2 loại là ASC và DESC

- ASC là Tăng dần
- DESC Giảm dần

## GROUP BY

- Câu lệnh GROUP BY nhóm các hàng có cùng giá trị thành các hàng tóm tắt, như "tìm số lượng khách hàng ở mỗi quốc gia".
- Câu lệnh GROUP BY thường được sử dụng với các hàm tổng hợp (COUNT, MAX, MIN, SUM, AVG) để nhóm tập hợp kết quả theo một hoặc nhiều cột.
- thường thì mình lấy tất cả id của group và sử dụng sql lồng

```sql
SELECT Tên cột (s)
FROM Tên Bảng
WHERE Điều Kiện
GROUP BY Tên cột (s)
ORDER BY Tên cột (s);
```

- bạn cứ tưởng tượng là nó sẽ chia các thành phần và nhóm nó thành một nhóm tất cả các thành phần ấy sẽ đứng gần nhau (giống như 1 đống đỗ đỏ 1 đống đỗ đen ..... chẳng hạn bình thường thì chúng trộn lẫn với nhau nhưng có cô tấm < Groub > phân chia chúng ra , nhớ đỗ đen thì có tính chất khác đỗ đỏ tuy chúng nằm trên 1 bảng đỗ nhé , rồi đùng hỏi tại sao nó lỗi heheehe)
