# BULK Import

SQL Server cung cấp câu lệnh BULK INSERT để thực hiện nhập dữ liệu lớn vào SQL Server bằng T-SQL.

Chèn hàng loạt là một quy trình hoặc phương pháp được cung cấp bởi hệ thống quản lý cơ sở dữ liệu để tải nhiều hàng dữ liệu vào một bảng cơ sở dữ liệu ”. Nếu chúng ta điều chỉnh giải thích này theo câu lệnh BULK INSERT, chèn hàng loạt cho phép nhập các tệp dữ liệu bên ngoài vào SQL Server

Giả sử rằng tổ chức của chúng ta có tệp CSV gồm 15.000.000 hàng và chúng ta muốn nhập tệp này vào một bảng cụ thể trong SQL Server, vì vậy chúng ta có thể dễ dàng sử dụng câu lệnh BULK INSERT trong SQL Server. Chắc chắn, chúng ta có thể tìm thấy một số phương pháp nhập để xử lý quy trình nhập tệp CSV này, ví dụ: chúng ta có thể sử dụng bcp (chương trình sao chép hàng loạt), SQL Server Import and Export Wizard hoặc SQL Server Integration Service. Tuy nhiên, câu lệnh BULK INSERT nhanh hơn và mạnh mẽ hơn nhiều so với việc sử dụng các phương pháp khác. Một ưu điểm khác của câu lệnh chèn hàng loạt là nó cung cấp một số tham số giúp xác định cài đặt của quá trình chèn hàng loạt. 

Nhưng theo tôi thấy với dữ liệu quan trọng thì ...... khá là nguy hiểm.

Csv là gì? csv (File Comma Separated Values) là phần mở rộng của file Excel được ngăn cách bằng dấu nhưng đôi khi cũng sử dụng những ký tự khác, như dấu chấm phẩy.Là file plain text chứa danh sách dữ liệu. Các file này thường được sử dụng để trao đổi dữ liệu giữa các ứng dụng khác nhau. 

Syntax basic 

```
BULK INSERT [Table]
FROM '*.csv'
```

## BULK INSERT with options
## BULK INSERT
## Reading entire content of file using OPENROWSET(BULK)
## Read json file using OPENROWSET(BULK)