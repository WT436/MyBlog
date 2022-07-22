# Data Clumps (Các khối dữ liệu bị vón cục)

- Đôi khi các phần khác nhau của Code chứa các nhóm biến giống hệt nhau (chẳng hạn như các tham số để kết nối với cơ sở dữ liệu). 
- Các khối này nên được chuyển thành các Class riêng của chúng.

![image](https://user-images.githubusercontent.com/63473793/121805966-de702c80-cc77-11eb-82c8-90c42e26ace1.png)

## Dấu Hiệu Cảnh Báo
- Thường thì những nhóm dữ liệu này là do cấu trúc chương trình kém hoặc "lập trình copypasta".
- Nếu bạn muốn chắc chắn liệu một số dữ liệu có phải là một nhóm dữ liệu hay không, chỉ cần xóa một trong các giá trị dữ liệu và xem liệu các giá trị khác có còn ý nghĩa hay không. Nếu không đúng như vậy, đây là một dấu hiệu tốt cho thấy nhóm biến này nên được kết hợp thành một đối tượng.
## Trả đũa cho một Class có mùi khó chịu.
- Cải thiện sự hiểu biết và tổ chức mã. Các thao tác trên dữ liệu cụ thể hiện được tập hợp tại một nơi duy nhất, thay vì một cách ngẫu nhiên trong toàn bộ mã.
- Giảm kích thước mã.
- 
 ![image](https://user-images.githubusercontent.com/63473793/121806024-327b1100-cc78-11eb-9447-eb166d2b85bd.png)