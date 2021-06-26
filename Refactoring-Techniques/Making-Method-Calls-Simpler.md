# Making Method Calls Simpler

Những kỹ thuật này làm cho việc gọi method trở nên đơn giản và dễ hiểu hơn. Điều này, đến lượt nó, đơn giản hóa các giao diện cho sự tương tác giữa các class.

1. Rename method 

Tên của một phương pháp không tiết lộ mục đích của nó. Thay đổi tên của method.

2. Add parameter

Một method cần thêm thông tin từ người gọi của nó. Thêm một Parameter cho một object có thể truyền thông tin này.

3. Remove parameter

Một Parameter không còn được sử dụng bởi thân method. Loại bỏ nó.

4. Separate Query from Modifier 

Chúng ta có một method trả về một giá trị nhưng cũng thay đổi trạng thái của một object. Tạo hai method, một method cho truy vấn và một method sửa đổi.

5. Parameterise Method 

Một số method thực hiện những điều tương tự nhưng với các giá trị khác nhau được chứa trong thân method. Tạo một method sử dụng một Parameter cho các giá trị khác nhau.

6. Replace Parameter with Explicit Methods 

Chúng ta có một method chạy code khác nhau tùy thuộc vào các giá trị của một Parameter được liệt kê. Tạo một method riêng cho từng giá trị của Parameter.

7. Preserve Whole Object

Chúng ta đang nhận được một số giá trị từ một object chuyển các giá trị này làm Parameter trong một lời gọi method. Gửi toàn bộ object thay thế.

8. Replace Parmeter With Method 

Một object gọi một method, sau đó chuyển kết quả làm Parameter cho một method. Người nhận cũng có thể gọi method này. Loại bỏ Parameter và để người nhận gọi method của nó.

9. Introduce Parameter Object

Chúng ta có một nhóm các Parameter đi cùng nhau một cách tự nhiên. Thay thế chúng bằng một object.

10. Remove Setting Method 

Một field phải được đặt tại thời điểm tạo và không bao giờ được thay đổi. Loại bỏ bất kỳ method thiết lập nào cho field đó (đặt nó vào method khởi tạo nếu cần)

11. Hide Method

Một method không được sử dụng bởi bất kỳ class nào khác. Đặt method ở chế độ private.

12. Replace Constructor with Facftory Method

Chúng ta muốn làm nhiều việc hơn là build đơn giản khi Chúng ta tạo một object. Thay thế hàm tạo bằng một method gốc.

13. Encapsulate Downcast 

Một method trả về một object cần được người gọi của nó từ chối. Di chuyển downcast đến bên trong method.

14. Replace Error code with Exception

Một method trả về một code đặc biệt để chỉ ra lỗi. Thay vào đó, hãy ném một ngoại lệ.

15. Replace Exception with Test

Chúng ta đang ném một ngoại lệ đã kiểm tra với một điều kiện mà người gọi có thể đã kiểm tra trước. Thay đổi người gọi để thực hiện kiểm tra trước.

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>