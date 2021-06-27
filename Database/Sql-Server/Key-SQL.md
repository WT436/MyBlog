# Các từ khóa SQL

## Lấy dữ liệu

# Các từ khóa SQL

## Lấy dữ liệu

Thao tác sử dụng nhiều nhất trong một cơ sở dữ liệu dựa trên giao dịch là thao tác lấy dữ liệu.

SELECT được sử dụng để lấy dữ liệu từ một hoặc nhiều bảng trong cơ sở dữ liệu, SELECT là lệnh thường dùng nhất của ngôn ngữ sửa đổi dữ liệu (tạm dịch) (tiếng Anh: Data Manipulation Language - DML).

<br/>Trong việc tạo ra câu truy vấn SELECT, người sử dụng phải đưa ra mô tả cho những dữ liệu mình muốn lấy ra chứ không chỉ ra những hành động vật lý nào bắt buộc phải thực hiện để lấy ra kết quả đó.

<br/>Hệ thống cơ sở dữ liệu, hay chính xác hơn là bộ tối ưu hóa câu truy vấn sẽ dịch từ câu truy vấn sang kế hoạch truy vấn tối ưu.
Những từ khóa liên quan tới SELECT bao gồm:

- FROM dùng để chỉ định dữ liệu sẽ được lấy ra từ những bảng nào, và các bảng đó quan hệ với nhau như thế nào.
- WHERE dùng để xác định những bản ghi nào sẽ được lấy ra, hoặc áp dụng với GROUP BY.
- GROUP BY dùng để kết hợp các bản ghi có những giá trị liên quan với nhau thành các phần tử của một tập hợp nhỏ hơn các bản ghi.
- HAVING dùng để xác định những bản ghi nào, là kết quả từ từ khóa GROUP BY, sẽ được lấy ra.
- ORDER BY dùng để xác định dữ liệu lấy ra sẽ được sắp xếp theo những cột nào.
  <br/> Ví dụ sau về việc sử dụng câu lệnh SELECT để lấy danh sách những cuốn sách có giá trị. Câu truy vấn này sẽ truy lục tất cả các bản ghi trong bảng books với giá trị của cột price lớn hơn 100.00. Kết quả sẽ được sắp xếp theo thứ tự tăng dần của các giá trị trong cột title. Dấu (\*) trong phần select list cho biết tất cả các cột của bảng books sẽ được lấy ra và thể hiện ở kết quả.

```sql
SELECT *
FROM books
WHERE price > 100.00
ORDER BY title;
```

Ví dụ sau giải thích cách liên kết nhiều bảng, tập hợp các bản ghi trong câu truy vấn SQL, nó sẽ trả về danh sách các cuốn sách và số tác giả của từng cuốn sách.

```Sql
SELECT books.title, count(*) AS Authors
FROM books
JOIN book_authors
ON books.isbn = book_authors.isbn
GROUP BY books.title;
```

Kết quả của ví dụ trên giống như sau:

```console
Title Authors
---------------------- -------
SQL Examples and Guide 3
The Joy of SQL 1
How to use Wikipedia 2
Pitfalls of SQL 1
How SQL Saved my Dog 1
```

(Ký tự gạch chân "\_" thường được sử dụng trong tên bảng và tên cột để phân cách các từ vì các ký tự khác có thể mâu thuẫn với cú pháp SQL. Ví dụ như, dấu "-" có thể được hiểu là dấu trừ.)

Với điều kiện cột isbn là cột chung duy nhất của hai bảng và cột title chỉ tồn tại trong bảng books thì câu truy vấn trên có thể được viết lại theo mẫu sau:

```sql
SELECT title, count(*) AS Authors
FROM books
NATURAL JOIN book_authors
GROUP BY title;
```

Tuy nhiên nhiều nhà cung cấp không hỗ trợ các thức này, hoặc nó yêu cầu một số quy ước về tên cột nào đó. Như vậy, câu truy vấn trên không được phổ biến.

## Sửa đổi dữ liệu

Ngôn ngữ sửa đổi dữ liệu (Data Manipulation Language - DML), là một phần nhỏ của ngôn ngữ, có những thành phần tiêu chuẩn dùng để thêm, cập nhật và xóa dữ liệu delete data.

- INSERT dùng để thêm dữ liệu vào một bảng đã tồn tại.
- UPDATE dùng để thay đổi giá trị của một tập hợp các bản ghi trong một bảng.
- MERGE dùng để kết hợp dữ liệu của nhiều bảng. Nó được dùng như việc kết hợp giữa hai phần tử INSERT và UPDATE.
- DELETE xóa những bản ghi tồn tại trong một bảng.
- TRUNCATE Xóa toàn bộ dữ liệu trong một bảng (không phải là tiêu chuẩn, nhưng là một lệnh SQL phổ biến).
  Nguồn : https://en.wikipedia.org/wiki/SQL , vào thực tế sẽ là mình quất nó
