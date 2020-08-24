# CSS là gì?

CSS là viết tắt của Cascading Style Sheets

- CSS mô tả cách các phần tử HTML được hiển thị trên màn hình, giấy hoặc trong các phương tiện khác
- CSS tiết kiệm rất nhiều công việc.
- Nó có thể kiểm soát bố cục của nhiều trang web cùng một lúc Các bảng định kiểu bên ngoài được lưu trữ trong các tệp CSS

## Tại sao phải dùng css

- không dùng có mà tết ak ,đơn giản bạn thích gái xấu hay gái xinh
- cái gì nó có thể sử lý đk cho nó đẹp chúng ta dùng tất

## cấu trúc

- selector {thuộc tính : giá trị thuộc tính ;}

### selector là gì

- selector CSS được sử dụng để "tìm" (hoặc chọn) các phần tử HTML bạn muốn tạo kiểu.
- Chúng ta có thể chia các selector CSS thành năm loại:
- selector đơn giản (chọn các phần tử dựa trên tên, id, lớp)
- selector bộ kết hợp (chọn phần tử dựa trên mối quan hệ cụ thể giữa chúng)
- selector lớp giả (chọn phần tử dựa trên một trạng thái nhất định)
- selector phần tử giả (chọn và tạo kiểu cho một phần của phần tử)
- selector thuộc tính (chọn các phần tử dựa trên một thuộc tính hoặc giá trị thuộc tính)

# Thêm css vào html

- có 3 cách thêm css vào file trong html

1. thêm trực tiếp vào thẻ

```console
<b style="color: red">My Name is Nam</b>
```

2. thêm một thẻ style

```console
<style>
b{
color : blue;
}
</style>
<b>My Name is Nam</b>
```

3. tạo 1 file css và add link vào html

```console
<link rel="stylesheet" type="text/css" href="DayLaCssCuaNam.css">
```

## thứ tự ưu tiên 1>2>3

## Comments

```console
/* Đây là đoạn comment css */
hoặc
/* Đây là
đoạn
comment css */
bên style của html cx làm tương tự
```

## mã màu

- gồm có 3 Dạng là : RGB , HEX , HSL
