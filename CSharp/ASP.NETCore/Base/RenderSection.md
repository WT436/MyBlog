# RenderSection trong asp.net .net core

1. RenderSection là thành phần cung cấp bộ file dùng chung cho các trang kết nối đến nó

- các file thường có rất nhiều thành phần dùng chung vd như menu , footer ......
- nếu như dự dụng các thành phần này dùng đi dùng lại thì thực sự rất lãng phí

2. vậy cần dùng 1 layout chung cho các trang có cùng cấu trúc

```console
quy ước đặt tên
- dấu gạch chân trước tên của file thường dùng cho một số file đặc biệt  như Razor .... để phân biệt file bình thường
```

3. @RenderBody() là thành phần ghép trang cần thành phần dùng chung và thành phần cần ghép ,nơi đây chính là vị trí mà các trang bổ xung với layout
4. nội dung thay thế cần có

```console
@{
    Layout = "_layout";
    ViewData["Title"]=["Index"] ;
}
```

5. ViewStart
6. tùy chỉnh css js nội dung layout

```console
  bên layout khai báo   @RenderSection("css", required: false)
  bên view con : @section Test
{
    nội dung
}
```
