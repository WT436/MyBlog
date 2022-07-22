# Moving Features Between Objects

Ngay cả khi bạn đã phân phối chức năng giữa các class khác nhau theo cách kém hoàn hảo thì vẫn có hy vọng.

Các kỹ thuật tái cấu trúc này chỉ ra cách di chuyển chức năng giữa các class một cách an toàn, tạo các class mới và ẩn các chi tiết triển khai khỏi truy cập công khai.

1. Move method 

Một method đang hoặc sẽ được sử dụng hoặc được sử dụng bởi nhiều tính năng của một class khác hơn là class mà nó được định nghĩa. Tạo một method mới với phần thân tương tự trong class mà nó sử dụng nhiều nhất. Chuyển method cũ thành một ủy quyền đơn giản hoặc xóa nó hoàn toàn.

2. Move field 

Một field, đang hoặc sẽ được, sử dụng bởi một class khác nhiều hơn class mà nó được định nghĩa. Tạo một field mới trong class mục tiêu và thay đổi tất cả người dùng của nó.

3. Extract Class

Bạn có một class đang làm công việc cần được thực hiện bởi hai class. Tạo một class mới và di chuyển các field và method có liên quan từ class cũ sang class mới.

4. Inline Class 

Một class học không thực hiện được nhiều. Di chuyển tất cả các tính năng của nó vào một class khác và xóa nó.

5. Hide Delegate 

Một client đang gọi một class đại biểu của một object. Tạo các method trên server để Hide Delegate.

6. Remove Middle Man

Một class đang thực hiện ủy quyền quá đơn giản. Yêu cầu khách hàng gọi trực tiếp cho người được ủy quyền.

7. Introduce Foreign Method

server class bạn đang sử dụng cần một method bổ sung, nhưng bạn không thể sửa đổi class đó. Tạo một method trong class Client với một bản sao của server class làm method đầu tiên của nó.

8. Introduce Local Extension

Một class server mà bạn đang sử dụng cần một số method bổ sung, nhưng bạn không thể sửa đổi class đó. Tạo một class mới chứa các method trích xuất đó. Đặt class tiện ích mở rộng này thành class con hoặc class bao bọc của class gốc.

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>