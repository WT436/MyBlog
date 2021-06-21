# Long Parameter List

- Nhiều hơn ba hoặc bốn tham số cho một Method.
- ![image](https://user-images.githubusercontent.com/63473793/121805856-4114f880-cc77-11eb-9bc6-8275e5c8486a.png)

## Dấu Hiệu Cảnh Báo


## Vậy chúng ta phải ứng sử với nó như thế nào?

Số lượng tham số của hàm không được lớn hơn 3
- Hàm không có tham số: rất tốt
- Hàm có một tham số: tốt
- Hàm có 2 tham số: được. Nhưng nên cân nhắc việc chuyển đổi hàm về dạng 1 tham số nếu có thể
- Hàm có 3 tham số: chấp nhận được. Tuy nhiên không khuyến khích.
Vì khi hàm có 3 tham số, có nghĩa là số test case viết test cho hàm đó là rất nhiều.
- Hàm có 4 tham số trở lên: rất tồi
Do đó giải pháp nâng cao chất lượng hàm là:
- Nếu hàm có 2 tới 3 tham số, luôn luôn cố gắng xem có thể biến đổi về dạng hàm có 0 hoặc 1 tham số không. 
Trường hợp thực sự cần thiết mới cho phép 2 tới 3 tham số.
- Nếu hàm có nhiều hơn 3 tham số, thì các tham số nên được nhóm vào trong một object/data structure.