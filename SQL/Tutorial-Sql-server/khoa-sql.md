# Khóa chính và khoá ngoại

- Các khoá chính và khóa ngoại là hai loại ràng buộc có thể được sử dụng để thực thi toàn vẹn dữ liệu trong các bảng SQL Server. Đây là những đối tượng cơ sở dữ liệu quan trọng.

## Khoá chính

- Khóa chính (hay ràng buộc khóa chính) được sử dụng để định danh duy nhất mỗi record trong table của cơ sở dữ liệu.
- Ngoài ra, nó còn dùng để thiết lập quan hệ 1-n (hay ràng buộc tham chiếu) giữa hai table trong cơ sở dữ liệu.
- Dữ liệu (value) của field khóa chính phải có tính duy nhất. Và không chứa các giá trị Null.
- Mỗi table nên chỉ có một khóa chính, khóa chính có thể tạo ra từ nhiều field của table.
- một khóa chính có thể 1 trường hoặc nhiều trường , hiểu là nhà thì có thể cả vợ cả chồng chùng chung sức thì mới ra quyết định chẳng hạn

```sql
cot1 kieu_du_lieu  PRIMARY KEY ,
hoặc
CONSTRAINT ten_rang_buoc PRIMARY KEY (cot1, cot2, … cot_n)
```

## Khóa ngoại

- Khóa ngoại của một table được xem như con trỏ trỏ tới khóa chính của table khác.
- Nếu trường MaSV của table DiemSV được sử dụng để tạo ràng buộc tham chiếu đến table HSSV, thông qua khóa chính là - MaSV thì MaSV của table DiemSV được gọi là khóa ngoại của bảng này. Đây cũng chính là lý do mà ta nói, khóa ngoại - được xem như con trỏ trởi tới khóa chính.

- hiểu đơn giản như sau muốn biết ai là chủ 1 bảng ta dùng khóa chính , (Nhà thì phải có lóc )
- muốn mời 1 nhà đến dự tiệc quan trong nhất thì phải mời chủ nhà ,khóa ngoại mời khóa chính
  cú pháp

```sql
CREATE TABLE bang_con
 (
  cot1 kieudulieu [ NULL | NOT NULL ],
  cot2 kieudulieu [ NULL | NOT NULL ],
  …

  CONSTRAINT fk_ten
   FOREIGN KEY (cot_con1, cot_con2, … cot_con_n)
   REFERENCES bang_me (cot_me1, cot_me2, … cot_me_n)
   [ ON DELETE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]
   [ ON UPDATE { NO ACTION | CASCADE | SET NULL | SET DEFAULT } ]
 );
```

- bang_con : Tên của bảng con muốn tạo.

- cot1, cot2 : Cột muốn tạo trong bảng. Mỗi cột có 1 loại dữ liệu, phải được chỉ định là chứa giá trị NULL hay NOT NULL, nếu không sẽ mặc định là NULL.Các kiểu dữ liệu trong SQL Server
- fk_ten : : Tên của ràng buộc khóa ngoại muốn tạo.
- cot_con1, cot_con2, … cot_con_n : Cột trong bang_con muốn tham chiếu tới khóa chính trong bang_me.
- bang_me : Tên của bảng mẹ chứa khóa chính được dùng trong bang_con.
- cot_me1, cot_me2, … cot_me_n : Cột tạo nên khóa chính trong bang_me. Khóa ngoại sẽ tạo ràng buộc giữa dữ liệu và các cột cot_con1, cot_con2, … cot_con_n trong bang_con.
- ON DELETE : Tùy chọn. Cho biết sẽ làm gì với dữ liệu con khi dữ liệu mẹ bị xóa. Có các lựa chọn NO ACTION, CASCADE, SET NULL và SET DEFAULT.
- ON UPDATE : Tùy chọn. Cho biết sẽ làm gì với dữ liệu con khi dữ liệu mẹ được cập nhật. Có các lựa chọn NO ACTION, CASCADE, SET NULL và SET DEFAULT.
- NO ACTION : Dùng với ON DELETE hoặc ON UPDATE, nghĩa là không làm gì với dữ liệu con khi dữ liệu mẹ bị xóa hoặc cập nhật.
- CASCADE : Dùng với ON DELETE hoặc ON UPDATE, nghĩa là dữ liệu con bị xóa hoặc cập nhật khi dữ liệu mẹ bị xóa hoặc cập nhật.
- SET NULL : Dùng với ON DELETE hoặc ON UPDATE, nghĩa là dữ liệu con được đặt là NULL khi dữ liệu mẹ bị xóa hoặc cập nhật.
- SET DEFAULT : Dùng với ON DELETE hoặc ON UPDATE, nghĩa là dữ liệu con được đặt thành giá trị mặc định khi dữ liệu mẹ bị xóa hoặc cập nhật.
