# Backup and Restore Database

Backup là một bản sao lưu dữ liệu/cơ sở dữ liệu. Việc sao lưu CSDL trong MS SQL Server là rất quan trọng để bảo vệ dữ liệu trước việc mất CSDL. Có 3 hình thức sao lưu chính trong MS SQL Server là Full/Database, Differential/Incremental, Transactional Log/Log.

## Backup 

1. Sao lưu database bằng T-SQL

- Full/Database

```sql
Backup database <TEN DATABASE> to disk = '<DUONG DAN FILE BACKUP + TEN FILE>'
```

- Differential/Incremental
```sql
Backup database <TEN DATABASE> to
disk = '<DUONG DAN FILE BACK UP + TEN FILE>' with differential
```

- Transactional Log/Log
```sql
Backup log <TEN DATABASE> to disk = '<DUONG DAN FILE BACKUP + TEN FILE>'
```

2. SSMS

-  Mở SQL Server Management Studio (SSMS) và kết nối
-  Mở rộng phần Database 
-  Nhấp chuột phải vào cơ sở dữ liệu bạn muốn sao lưu, sau đó chọn Tasks > Back up.

![image](https://user-images.githubusercontent.com/63473793/123633299-3b0c4380-d843-11eb-9624-865289f6f0ce.png)

-  Trên cửa sổ Cơ sở dữ liệu sao lưu, đảm bảo trường Cơ sở dữ liệu chứa tên của cơ sở dữ liệu bạn muốn sao lưu.
-  Chọn Backup Type. Theo mặc định, nó là Full - hãy để nó ở chế độ đó.
-  Nhấp vào Remove để xóa tên tệp sao lưu mặc định / cuối cùng.
-  Bấm Add để mở cửa sổ Chọn Đích Dự phòng.
-  Nhấp vào [...] bên cạnh trường Tên tệp.
-  rên cửa sổ Định vị Tệp Cơ sở dữ liệu, chọn thư mục mà bạn muốn tệp sao lưu đi đến. Theo mặc định, nó là ..\ Microsoft SQL Server\MSSQL.1\MSSQL\Backup.

Bên cạnh đó chúng ta cũng có thể tạo ra các file Generate Script để tạo thành các file .sql (Nhớ là cả data , nó mặc định chỉ có khung).

## Restore

Khôi phục là quá trình sao chép dữ liệu đã sao lưu và đưa các giao dịch được ghi lại vào dữ liệu của MS SQL Server. Hiểu đơn giản, đây là quá trình lấy file sao lưu và đưa nó trở lại CSDL.

Khôi phục CSDL có thể được thực hiện bằng 2 cách.

1. Sử dụng T-SQL

Cú pháp dưới đây được dùng để khôi phục CSDL.

```sql 
Restore database <Your database name> from disk = '<Backup file location + file name>'
```

2. SSMS

- Kết nối tới CSDL và click chuột phải vào thư mục Database , chọn Restore Database để hiện ra như hình dưới đây.

![image](https://user-images.githubusercontent.com/63473793/123633969-0d73ca00-d844-11eb-9861-3ae07f276d02.png)

- Chọn Device và chọn đường dẫn để mở tập tin sao lưu như trong hình dưới đây.

![image](https://user-images.githubusercontent.com/63473793/123634005-18c6f580-d844-11eb-9664-55347ed15cd4.png)

- Click OK và màn hình dưới đây sẽ hiện ra.

![image](https://user-images.githubusercontent.com/63473793/123634046-25e3e480-d844-11eb-9e60-525fd009813c.png)

- Chọn Files ở góc bên trái màn hình, hộp thoại dưới đây sẽ hiện ra.

![image](https://user-images.githubusercontent.com/63473793/123634074-3005e300-d844-11eb-907b-4afc5878e64b.png)

- Chọn Options ở góc trái và click OK để bắt đầu khôi phục CSDL TestDB như trong hình dưới đây.

![image](https://user-images.githubusercontent.com/63473793/123634114-398f4b00-d844-11eb-9e55-cbdcf03d462b.png)
