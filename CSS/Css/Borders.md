# Borders

- Thuộc tính Borders CSS cho phép bạn chỉ định kiểu, chiều rộng và màu sắc của đường viền của một phần tử.
- nó giúp bạn tạo một đường viền bao quanh phần tử
- các thuộc tính của nó

- Cú Pháp Tổng quan

```css
border: border-color border-width border-style;
```

## border-style

```console
dotted : Xác định đường viền có dấu chấm
dashed  - Xác định đường viền đứt nét
solid - Xác định đường viền chắc chắn
double - Xác định đường viền kép
groove  - Xác định đường viền có rãnh 3D. Hiệu ứng phụ thuộc vào giá trị màu viền
ridge - Xác định đường viền 3D. Hiệu ứng phụ thuộc vào giá trị màu viền
inset - Xác định đường viền chèn 3D. Hiệu ứng phụ thuộc vào giá trị màu viền
outset - Xác định đường viền ban đầu 3D. Hiệu ứng phụ thuộc vào giá trị màu viền
none - Xác định không có đường
hidden  - Xác định một đường viền ẩn
```

## border-width

- Thuộc tính border-width chỉ định chiều rộng của bốn đường viền.
- Chiều rộng có thể được đặt thành một kích thước cụ thể (tính bằng px, pt, cm, em, v.v.) hoặc bằng cách sử dụng một trong ba giá trị được xác định trước: mỏng, trung bình hoặc dày

## Border Color

- Thuộc tính màu viền được sử dụng để đặt màu của bốn đường viền.
- Màu có thể được đặt bằng:
- Name - chỉ định tên màu, như "đỏ"
- HEX - chỉ định một giá trị HEX, như "# ff0000"
- RGB - chỉ định một giá trị RGB, như "rgb (255,0,0)"
- HSL - chỉ định một giá trị HSL, như "hsl (0, 100%, 50%)" trong suốt
- Lưu ý: Nếu màu viền không được đặt, nó sẽ kế thừa màu của phần tử.

## border-radius

- dùng để bo tròn 4 cạnh của border
- border-radius: giá trị bo;
- VD : border-radius: 5px;

```console
border Đặt tất cả các thuộc tính đường viền trong một khai báo
border-bottom Đặt tất cả các thuộc tính đường viền dưới cùng trong một khai báo
border-bottom-color Đặt màu của đường viền dưới cùng
border-bottom-style Đặt kiểu cho đường viền dưới cùng
border-bottom-width Đặt chiều rộng của đường viền dưới cùng
border-color Đặt màu của bốn đường viền
border-left Đặt tất cả các thuộc tính viền trái trong một khai báo
border-left-color Đặt màu của đường viền bên trái
border-left-style Đặt kiểu viền trái
border-left-width Đặt chiều rộng của đường viền bên trái
border-radius Đặt tất cả thuộc tính bốn đường viền - * - radius cho các góc tròn
border-right Đặt tất cả các thuộc tính đường viền bên phải trong một khai báo
border-right-color Đặt màu của đường viền bên phải
border-right-style Đặt kiểu viền phải
border-right-width Đặt chiều rộng của đường viền bên phải kiểu đường viền Đặt kiểu của 4 đường viền
border-top Đặt tất cả các thuộc tính đường viền trên cùng trong một khai báo
border-top-color Đặt màu của đường viền trên cùng
border-top-style Đặt phong cách của đường viền trên cùng
border-top-width Đặt chiều rộng của đường viền trên cùng
border-width Đặt chiều rộng của bốn đường viền
```
