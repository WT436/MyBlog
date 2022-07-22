# Linear Gradients

- CSS gradient cho phép bạn hiển thị các chuyển tiếp mượt mà giữa hai hoặc nhiều màu được chỉ định.
  cấu trúc

```console
background-image: linear-gradient(direction, color-stop1, color-stop2, ...);
background-image: linear-gradient(to bottom right, red, yellow);
background-image: linear-gradient(-90deg, red, yellow);
background-image: linear-gradient(red, yellow, green);
background-image: linear-gradient(to right, red,orange,yellow,green,blue,indigo,violet);
background-image: repeating-linear-gradient(red, yellow 10%, green 20%);
```

- Để tạo một gradient tuyến tính, bạn phải xác định ít nhất hai điểm dừng màu. Điểm dừng màu là những màu bạn muốn tạo ra các chuyển tiếp mượt mà. Bạn cũng có thể đặt điểm bắt đầu và hướng (hoặc góc) cùng với hiệu ứng gradient.

## Radial Gradients

- Một Radial Gradients được xác định bởi tâm của nó.
- Để tạo Radial Gradients, bạn cũng phải xác định ít nhất hai điểm dừng màu.

```console
 closest-side : Hình dạng kết thúc của gradient gặp mặt của hộp gần tâm nhất (đối với hình tròn) hoặc gặp cả mặt dọc và ngang gần tâm nhất (đối với hình elip).

 closest-corner : Hình dạng kết thúc của gradient có kích thước sao cho nó tiếp xúc chính xác với góc gần nhất của hộp tính từ tâm của nó.

 farthest-side : Tương tự như cạnh gần nhất, ngoại trừ hình dạng kết thúc có kích thước để đáp ứng các cạnh của hộp xa tâm nhất (hoặc các cạnh dọc và ngang).

 farthest-corner : Giá trị mặc định, hình dạng kết thúc của gradient được định kích thước sao cho nó đáp ứng chính xác góc xa nhất của hộp tính từ tâm của nó.
```

-- tương tự như Linear Gradients
```css
background-image: radial-gradient(shape size at position, start-color, ..., last-color);
background-image: radial-gradient(red, yellow, green);
background-image: radial-gradient(red 5%, yellow 15%, green 60%);
background-image: radial-gradient(circle, red, yellow, green);
background-image: radial-gradient(closest-side at 60% 55%, red, yellow, black);
background-image: radial-gradient(farthest-side at 60% 55%, red, yellow, black);
background-image: repeating-radial-gradient(red, yellow 10%, green 15%);
```
