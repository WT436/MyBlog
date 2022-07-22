## Text Alignment

- Thuộc tính text-align được sử dụng để đặt căn lề ngang của văn bản.

```console
left	   text-align: left;	    Sắp nội dung theo chiều ngang nằm về bên trái, đây là dạng mặc định.
right	   text-align: right;	    Sắp nội dung theo chiều ngang nằm về bên phải.
center	   text-align: center;	    Sắp nội dung theo chiều ngang nằm giữa.
justify	   text-align: justify;  	Sắp xếp nội dung cho các dòng có chiều rộng bằng nhau.
inherit	   text-align: inherit; 	Xác định thừa hưởng thuộc tính từ thành phần cha (thành phần bao ngoài).
```

## Text Decoration

- Thuộc tính Text Decoration được sử dụng để đặt hoặc xóa trang trí khỏi văn bản.
- Giá trị text-decoration: none; thường được sử dụng để xóa gạch chân khỏi các liên kết:

```console
none	        text-decoration: none;          	Định dạng văn bản bình thường, đây là dạng mặc định.
underline	    text-decoration: underline;	        Xác định đường gạch bên dưới văn bản.
overline	    text-decoration: overline;      	Xác định đường gạch bên trên văn bản.
line-through	text-decoration: line-through;  	Xác định đường gạch ngang văn bản.
blink	        text-decoration: blink;	            Xác định văn bản nhấp nháy.
inherit	        text-decoration: inherit;	        Xác định thừa hưởng thuộc tính từ thành phần cha.
```

## Text Transformation

- text-transform thuộc tính được sử dụng để chỉ định chữ hoa và chữ thường trong văn bản.
- Nó có thể được sử dụng để biến mọi thứ thành chữ hoa hoặc chữ thường hoặc viết hoa chữ cái đầu tiên của mỗi từ:

```console
none	    text-transform: none;	    Trả văn bản về dạng mặc định ban đầu.
capitalize	text-transform: capitalize;	Chữ đầu tiên của mỗi thành phần là chữ hoa.
uppercase	text-transform: uppercase;	Tất cả chữ trong văn bản thành chữ hoa.
lowercase	text-transform: lowercase;	Tất cả chữ trong văn bản thành chữ thường.
inherit	    text-transform: inherit;	Xác định thừa hưởng thuộc tính từ thành phần cha.
```

## Text Spacing

- Text Spacing thuộc tính được sử dụng để chỉ định thụt lề của dòng đầu tiên của văn bản

1. Thuộc tính text-indent được sử dụng để chỉ định thụt lề của dòng đầu tiên của văn bản

- text-indent: 50px;

2. Letter Spacing thuộc tính được sử dụng để chỉ định khoảng cách giữa các ký tự trong văn bản.

- letter-spacing: 3px;

3. Line Height thuộc tính được sử dụng để chỉ định khoảng cách giữa các dòng

- line-height: 0.8;

4. Word Spacing

- thuộc tính được sử dụng để chỉ định khoảng cách giữa các từ trong văn bản
- word-spacing: 10px;

5. White Space thuộc tính chỉ định cách xử lý khoảng trắng bên trong một phần tử.

- white-space: nowrap;

## Text Shadow

- thuộc tính thêm bóng vào văn bản.
- text-shadow: 2px 2px;
- text-shadow: 2px 2px red;
- text-shadow: 2px 2px 5px red;
- cấu trúc : text-shadow: offset-x | offset-y | blur-radius | color
- nó có thể sếp trèn nhiều thuộc tính này

## all thuộc tính

```console
color	        Đặt màu cho văn bản
direction	    Chỉ định hướng văn bản / hướng viết
letter-spacing	Tăng hoặc giảm khoảng cách giữa các ký tự trong văn bản
line-height	    Đặt chiều cao dòng
text-align	    Chỉ định căn lề ngang của văn bản
text-decoration	Chỉ định trang trí được thêm vào văn bản
text-indent	    Chỉ định thụt lề của dòng đầu tiên trong khối văn bản
text-shadow	    Chỉ định hiệu ứng đổ bóng được thêm vào văn bản
text-transform	Kiểm soát cách viết hoa của văn bản
text-overflow	Chỉ định cách báo hiệu nội dung tràn không được hiển thị cho người dùng
unicode-bidi	Văn bản có nên được ghi đè để hỗ trợ nhiều ngôn ngữ trong cùng một tài liệu hay không
vertical-align	Đặt căn chỉnh theo chiều dọc của một phần tử
white-space	    Chỉ định cách xử lý khoảng trắng bên trong một phần tử
word-spacing	Tăng hoặc giảm khoảng cách giữa các từ trong văn bản
```
