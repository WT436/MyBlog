# Joins

- là sự kết hợp của 2 bảng có cùng liên kết khóa chính - ngoại với nhau , để có thể lấy ra điểm chung riêng giữa chúng

- trong sql chúng ta có các dạng của join như sau :

  - (INNER) JOIN: Trả về các bản ghi có giá trị phù hợp trong cả hai bảng
  - LEFT JOIN: Trả về tất cả các bản ghi từ bảng bên trái và các bản ghi đã khớp từ bảng bên phải
  - RIGHT JOIN: Trả về tất cả các bản ghi từ bảng bên phải và các bản ghi phù hợp từ bảng bên trái
  - FULL JOIN: Trả về tất cả các bản ghi khi có sự trùng khớp trong bảng bên trái hoặc bên phải

  - nhớ đơn giản mang tên cái nào thì lấy tất cả của nó và những cái liên quan đến nó (khóa ngoại của các record liên quan) của bảng còn lại

### inner join

- Trả về các bản ghi có giá trị phù hợp trong cả hai bảng
- nó sẽ lấy phần kẹp thịt của 2 bảng (tưởng tượng bánh mỳ chú pew :)) )
  cú pháp

```sql
SELECT tên cột(s)
FROM bảng 1
INNER JOIN bảng 2
ON bang1.cot1 = bảng2.cot2;--(đây là khóa  chính - ngoại giữa 2 bảng)
```

- lấy vd nhé : xã huyện tỉnh đi cho thân thuộc

```sql
select top (10) * from Tinh -- bảng đầu tiên
				  inner join Huyen --bảng số 2
				  on Tinh.IDTP = Huyen.IDTP -- tỉnh có khóa chính là IDTP trong huyện cx có khóa ngoại liên kết vs khóa chính của bảng tỉnh là IDTP
```

- kết quả

```console
IDTP |  NameTP           |IDQH  |    NameQH           | IDTP
1	 | Thành phố Hà Nội	 | 1	| Quận Ba Đình	      |   1
1	 | Thành phố Hà Nội	 | 2	| Quận Hoàn Kiếm      |   1
1	 | Thành phố Hà Nội	 | 3	| Quận Tây Hồ	      |   1
1	 | Thành phố Hà Nội	 | 4	| Quận Long Biên      |   1
1	 | Thành phố Hà Nội	 | 5	| Quận Cầu Giấy	      |   1
1	 | Thành phố Hà Nội	 | 6	| Quận Đống Đa	      |   1
1	 | Thành phố Hà Nội	 | 7	| Quận Hai Bà Trưng	  |   1
1	 | Thành phố Hà Nội	 | 8	| Quận Hoàng Mai	  |   1
1	 | Thành phố Hà Nội	 | 9	| Quận Thanh Xuân	  |   1
1	 | Thành phố Hà Nội	 | 16	| Huyện Sóc Sơn	      |   1
```

- dễ thấy IDTP chính là khóa chính của bảng Tỉnh và IDTP cuối cùng là của bảng Huyện , chúng giống nhau và tất cacr các bản ghi của Huyện là NameQH đều Xuất Hiện không thiếu 1 huyện vì đơn giản bảng ghi của huyện và thành phố thì có rất rất nhiều nhưng mà tỉnh hà nội chỉ có những huyện này mà thôi (hà nội nó còn nhiều nữa nhé x30 thì phải)

# left join

- tương tự như trên nhưng nó sẽ lấy tất cả của bảng 1 và những bản ghi có liên quan của bảng 2 ,những bản ghi không phù hợp nó sẽ để null

### cú pháp

```sql
select top (10) * from Tinh -- bảng đầu tiên
			  left join Huyen --bảng số 2
			  on Tinh.IDTP = Huyen.IDTP -- tỉnh có khóa chính là IDTP trong huyện cx có khóa ngoại liên kết vs khóa chính của bảng tỉnh là IDTP
```

# right join

- tương tự như trên nhưng nó sẽ lấy tất cả của bảng 2 và những bản ghi có liên quan của bảng 1,những bản ghi không phù hợp nó sẽ để null

### cú pháp

```sql
select top (10) * from Tinh -- bảng đầu tiên
			  right join Huyen --bảng số 2
			  on Tinh.IDTP = Huyen.IDTP -- tỉnh có khóa chính là IDTP trong huyện cx có khóa ngoại liên kết vs khóa chính của bảng tỉnh là IDTP
```

# full join

- tương tự như trên nhưng nó sẽ lấy tất cả của bảng 2 và bảng 1,những bản ghi không phù hợp nó sẽ để null

### cú pháp

```sql
select top (10) * from Tinh -- bảng đầu tiên
			  full OUTER join Huyen --bảng số 2
			  on Tinh.IDTP = Huyen.IDTP -- tỉnh có khóa chính là IDTP trong huyện cx có khóa ngoại liên kết vs khóa chính của bảng tỉnh là IDTP
              -- thật ra mình cx đếu bao h dùng đến cái này (một vài trường hợp cần nó )
```
