# Monster Class

Một lớp chứa nhiều fields/methods/lines code

## Dấu Hiệu Cảnh Báo

- Các Class học thường bắt đầu với quy mô nhỏ. Nhưng theo thời gian, chúng trở nên cồng kềnh khi chương trình phát triển.
- Cũng như trường hợp của các Method dài, các lập trình viên thường thấy việc đặt một tính năng mới vào một Class hiện có sẽ ít hơn so với việc tạo một Class mới cho đối tượng này.

## Vậy chúng ta phải ứng sử với nó như thế nào?

Khi một lớp đội quá nhiều hats (chức năng), hãy nghĩ đến việc chia nhỏ nó ra:
![image](https://user-images.githubusercontent.com/63473793/121805182-44f34b80-cc74-11eb-835e-dbde8ef9a826.png)
- Giải nén Class : sẽ giúp nếu một phần hành vi của Class lớn có thể được tách thành một thành phần riêng biệt.
- Chia Nhỏ Class : sẽ giúp ích nếu một phần hành vi của Class lớn có thể được thực hiện theo những cách khác nhau hoặc được sử dụng trong một số trường hợp hiếm hoi.
- Nén thành Interface : Nếu một Class lớn chịu trách nhiệm về Interface, bạn có thể cố gắng di chuyển một số dữ liệu và hành vi của nó sang một đối tượng miền riêng biệt. Khi làm như vậy, có thể cần phải lưu trữ bản sao của một số dữ liệu ở hai nơi và giữ cho dữ liệu nhất quán.
- Một file code không quá 500 dòng
- Sử dụng dòng trắng để phân tách các phần độc lập trong code
- Các dòng code liên quan tới nhau nên đứng gần nhau
- Biến nên được định nghĩa gần nơi nó được sử dụng
- Biến cục bộ nên để ở đầu hàm
- Biến đối tượng nên được đặt ở đầu class
- Biến đếm của vòng lặp nên được định nghĩa bên trong vòng lặp
- Các hàm phụ thuộc nhau nên được đặt gần nhau
- Hàm gọi đứng trước hàm được gọi
- if/else/while/for khi có một dòng lệnh bên trong, vẫn phải xuống dòng và đặt dòng lệnh của nó trong ngoặc {}

## Trả đũa cho một Class có mùi khó chịu.
- Việc tái cấu trúc các Class này giúp các nhà phát triển không cần phải nhớ một số lượng lớn các thuộc tính cho một Class. 
![image](https://user-images.githubusercontent.com/63473793/121805278-bdf2a300-cc74-11eb-850f-2f426d46c2fd.png)
- Trong nhiều trường hợp, việc chia nhỏ các lớp lớn thành các phần sẽ tránh được sự trùng lặp về Code và chức năng.