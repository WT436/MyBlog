# Mảng đa chiều

- Mảng hai chiều được tổ chức thành các dòng và cột, trong đó các dòng là được tính theo hàng ngang của mảng, và các cột được tính theo hàng dọc của mảng.
- Mảng ba chiều cũng có thể được tạo ra nhưng thường ít sử dụng do khó hình dung. Trong mảng ba chiều những dòng bây giờ là các mảng hai chiều.
- Ngôn ngữ C# hỗ trợ hai kiểu mảng đa chiều là:
- Mảng đa chiều cùng kích thước: trong mảng này mỗi dòng trong mảng có cùng kích thước với nhau. Mảng này có thể là hai hay nhiều hơn hai chiều.
- Mảng đa chiều không cùng kích thước: trong mảng này các dòng có thể không cùng kích thước với nhau.

1. Mảng đa chiều cùng kích thước

- Mảng đa chiều cùng kích thước còn gọi là mảng hình chữ nhật (rectanguler array).
- Trong mảng hai chiều cổ điển, chiều đầu tiên được tính bằng số dòng của mảng và chiều thứ hai được tính bằng số cột của mảng.
- Để khai báo mảng hai chiều, chúng ta có thể sử dụng cú pháp theo sau:
  < kiểu dữ liệu > [ , ] < tên mảng >
- Ví dụ để khai báo một mảng hai chiều có tên là myRectangularArray để chứa hai dòng và ba cột các số nguyên, chúng ta có thể viết như sau: int [ , ] myRectangularArray;
- Trong cú pháp này, dấu ngoặc vuông trong int[,] chỉ ra rằng đang khai báo một kiểu dữ liệu là mảng số nguyên, và dấu phẩy (,) chỉ ra rằng đây là mảng hai chiều (hai dấu phẩy khai báo mảng ba chiều, và nhiều hơn nữa). Việc tạo thể hiện thực sự của mảng ở lệnh new int[ rows,columns ] để thiết lập kích thước của mỗi chiều. Ở đây khai báo và tạo thể hiện được kết hợp với nhau.
- Chương trình khởi tạo tất cả các giá trị các thành phần trong mảng thông qua hai vòng lặp for. Lặp thông qua mỗi cột của mỗi dòng. Do đó, thành phần đầu tiên được khởi tạo là rectangularArray[ 0,0 ], tiếp theo bởi rectangularArray[ 0,1 ] và đến rectangularArray[ 0,2 ]. Một khi điều này thực hiện xong thì chương trình sẽ chuyển qua thực hiện tiếp ở dòng tiếp tục: rectangularArray[ 1,0 ], rectangularArray[ 1,1 ], rectangularArray[ 1,2 ]. Cho đến khi tất cả các cột trong tất cả các dòng đã được duyệt qua tức là tất cả các thành phần trong mảng đã được khởi tạo.
- Như chúng ta đã biết, chúng ta có thể khởi tạo mảng một chiều bằng cách sử dụng danh sách các giá trị bên trong dấu ngoặc ({}). Chúng ta cũng có thể làm tương tự với mảng hai chiều. Trong ví dụ sau khai báo mảng hai chiều rectangularArray, và khởi tạo các thành phần của nó thông qua các danh sách các giá trị trong ngoặc, sau đó in ra nội dung của nội dung.

2. Mảng đa chiều có kích khác nhau

- Cũng như giới thiệu trước kích thước của các chiều có thể không bằng nhau, điều này khác với mảng đa chiều cùng kích thước. Nếu hình dạng của mảng đa chiều cùng kích thước có dạng hình chữ nhật thì hình dạng của mảng này không phải hình chữ nhật vì các chiều của chúng không điều nhau.
- Khi chúng ta tạo một mảng đa chiều kích thước khác nhau thì chúng ta khai báo số dòng trong mảng trước. Sau đó với mỗi dòng sẽ giữ một mảng, có kích thước bất kỳ. Những mảng này được khai báo riêng. Sau đó chúng ta khởi tạo giá trị các thành phần trong những mảng bên trong.
  Trong mảng này, mỗi chiều là một mảng một chiều. Để khai báo mảng đa chiều có kích thước khác nhau ta sử dụng cú pháp sau, khi đó số ngoặc chỉ ra số chiều của mảng: < kiểu dữ liệu> [][] ...
  Chúng ta có thể khai báo mảng số nguyên hai chiều khác kích thước tên myJaggedArray như sau: int [][] myJaggedArray;
  Chúng ta có thể truy cập thành phần thứ năm của mảng thứ ba bằng cú pháp:

```c#
myJagged- Array [ 2 ] [ 4].
```
