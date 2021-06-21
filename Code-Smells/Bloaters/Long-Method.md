# Long Method

## Dấu Hiệu Cảnh Báo
Một phương thức chứa quá nhiều dòng mã. Nói chung, bất kỳ phương pháp nào dài hơn 60 dòng , hay một trang giấy sẽ khiến bạn bắt đầu đặt câu hỏi.

Anh chính đã từng nói với tôi. "Em phải làm đủ mọi cách để hàm của em làm sao khi in ra giấy thì nó phải nằm trên một mặt giấy. hay nó phải nằm trọn trong vùng khi nó hiển thị trên 1 màn hình tiêu chuẩn".

## Tại sao phải làm như vậy ?

Một cái gì đó luôn được thêm vào một Method nhưng không bao giờ được lấy ra. Vì viết Code dễ hơn đọc, nên “mùi” này vẫn không được chú ý cho đến khi Method này biến thành một con quái vật xấu xí, quá khổ.

Về mặt tinh thần, thường khó tạo một Method mới hơn là thêm vào Method thức hiện có: “Nhưng nó chỉ là hai dòng, không có ích gì khi tạo toàn bộ một Method chỉ dành cho điều đó…” Có nghĩa là một dòng khác được thêm vào và sau đó lại khác, sinh ra một mớ code spaghetti. (code dạng mỳ ống . nó thực sự rối rắm khi nó chín. Muốn hiểu điều này hãy ra chợ mua 1 gói mỳ spaghetti và về nấu nó lên . Nhận xét trước và sau khi Nấu)

## Vậy chúng ta phải ứng sử với nó như thế nào?

Theo nguyên tắc chung, nếu bạn cảm thấy cần phải nhận xét về điều gì đó bên trong một Method, bạn nên lấy Code này và đặt nó vào một Method mới. Ngay cả một dòng duy nhất cũng có thể và nên được tách thành một Method riêng biệt, nếu nó yêu cầu giải thích. Và nếu Method có tên mô tả, sẽ không ai cần nhìn vào mã để xem nó hoạt động gì.

![image](https://user-images.githubusercontent.com/63473793/121804803-5b98a300-cc72-11eb-98db-70534dfeed31.png)

- Để giảm độ dài của thân phương thức, hãy sử dụng Trích xuất Method.
- Nếu các biến và tham số cục bộ cản trở việc trích xuất một phương thức, hãy sử dụng giảm tải bằng Truy vấn, Parameter class hoặc Giữ gìn Object.
- Nếu không có công thức nào trước đây giúp ích, hãy thử chuyển toàn bộ phương thức sang một đối tượng riêng biệt thông qua Replace Method bằng Method Object.
- Các toán tử và vòng lặp có điều kiện là một manh mối tốt để mã có thể được chuyển sang một phương thức riêng biệt. Đối với các điều kiện, hãy sử dụng Decompose Conditional. Nếu các vòng lặp bị cản trở, hãy thử trích xuất Method.

## Thanh toán sòng phẳng với Method.
- Trong số tất cả các loại Code OOP, các Class có Method ngắn tồn tại lâu nhất. Một Method hoặc Function càng dài, thì càng khó hiểu và khó duy trì nó.
- Ngoài ra, các Method dài cung cấp nơi ẩn náu hoàn hảo cho các Code trùng lặp không mong muốn.
  ![image](https://user-images.githubusercontent.com/63473793/121804945-30628380-cc73-11eb-8295-d0798b48d6e0.png)

- Mỗi hàm chỉ làm một việc
- Tên hàm phải mô tả được các hành động mà hàm đó thực thi, tránh hiệu ứng lề
- Bố cục giảm dần
- Không được sử dụng output argument
- Không lặp code

## Hiệu Xuất Công Việc.
Việc tăng số lượng Method có làm ảnh hưởng đến hiệu suất như nhiều người khẳng định không? Trong hầu hết các trường hợp, tác động là không đáng kể đến mức nó thậm chí không đáng lo ngại.

Thêm vào đó, bây giờ bạn đã có Code rõ ràng và dễ hiểu, bạn có nhiều khả năng tìm thấy các Method thực sự hiệu quả để tái cấu trúc Code và nhận được hiệu suất thực sự nếu có nhu cầu.
