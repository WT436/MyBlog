# float và clear

- Thuộc tính float trong CSS chỉ định cách một phần tử nên float.
- Thuộc tính rõ ràng CSS chỉ định những phần tử nào có thể trôi nổi bên cạnh phần tử đã xóa và ở phía nào.

# float

- Thuộc tính float được sử dụng để định vị và định dạng nội dung, ví dụ: để một hình ảnh nổi bên trái văn bản trong vùng chứa.

```console
left	    float: left;	    Thành phần được trôi nổi (float) qua bên trái.
right	    float: right;	    Thành phần được trôi nổi (float) qua bên phải.
none	    float: none;	    Thành phần không được trôi nổi (float) qua bên phải hay trái, đây là dạng mặc định.
inherit	    float: inherit;	    Xác định thừa hưởng thuộc tính từ thành phần cha (thành phần bao ngoài).
```

# clear

- Thuộc tính clear xác định 2 bên của phần tử (left, right), nơi mà phần tử float không được cho phép (ngăn cản thành phần không được float trái, phải hay cả hai).

```console
tag {
    clear: giá trị;
}
left	    clear: left;	  Bên trái của thành phần không được float.
right	    clear: right;	  Bên phải của thành phần không được float.
both	    clear: both;	  Bên trái và phải của thành phần không được float.
none	    clear: none;	  Đây là mặc định của thành phần clear, bên trái và phải của thành phần được float.
inherit	    clear: inherit;	  Xác định thừa hưởng thuộc tính từ thành phần cha (thành phần bao ngoài).
```
