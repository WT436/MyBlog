# Organisation Data

Các kỹ thuật tái cấu trúc này giúp xử lý dữ liệu, thay thế các nguyên thủy bằng chức năng class phong phú. 

Một kết quả quan trọng khác là gỡ rối các liên kết class, điều này làm cho các class dễ di động hơn và có thể tái sử dụng.

1. Self-Encapsulate Field

Chúng ta đang truy cập trực tiếp vào một fields, nhưng việc ghép nối với fields đang trở nên khó khăn. Tạo các method nhận và thiết lập cho fields và chỉ sử dụng những method đó để truy cập fields.

2. Replace Data Value with Objects

Chúng ta có một mục dữ liệu cần dữ liệu hoặc hành vi bổ sung. Biến mục dữ liệu thành một object.

3. Change Value to Reference 

Chúng ta có một class với nhiều cá thể bằng nhau mà Chúng ta muốn thay thế bằng một object duy nhất. Biến object thành object tham chiếu.

4. Change Reference to Value

Chúng ta có một object tham chiếu nhỏ, không thể thay đổi và khó quản lý. Biến nó thành một object giá trị.

5. Replace Array With Object

Chúng ta có một mảng trong đó các phần tử nhất định có nghĩa là những thứ khác nhau. Thay thế mảng bằng một object có một fields cho mỗi phần tử.

6. Duplicate Observed Data 

Chúng ta chỉ có sẵn dữ liệu domain trong điều khiển GUI và các method domain cần có quyền truy cập. Sao chép dữ liệu vào một object domain. Thiết lập một trình quan sát để đồng bộ hóa hai phần dữ liệu.

7. Change Unidirectional Association to Bidirectional 

Chúng ta có hai class cần sử dụng các tính năng của nhau, nhưng chỉ có một liên kết một chiều. Thêm con trỏ quay lại và thay đổi công cụ sửa đổi để cập nhật cả hai bộ.

8. Change Bidirectional Association to Unidirectional

Chúng ta có một liên kết hai chiều nhưng một class không còn cần các tính năng của class kia nữa. Bỏ phần cuối không cần thiết của liên kết.

9. Replace Magic Number with Symbolic Constant 

Chúng ta có một số theo nghĩa đen với một ý nghĩa cụ thể. Tạo một const, đặt tên nó theo ý nghĩa và thay thế số bằng nó.

10. Ecnapsulate Field 

Có một lĩnh vực public. Đặt nó ở chế độ private và cung cấp người truy cập.

11. Encapsulate Collection 

Một method trả về một tập hợp. Làm cho nó trả về view readonly và cung cấp thêm / bớt các method.

12. Replace Record with Data Class

Chúng ta cần interface với cấu trúc bản ghi trong môi trường lập trình truyền thống. Tạo một object dữ liệu câm cho bản ghi

13. Replace Type Code with Class

Một class có code kiểu số không ảnh hưởng đến hành vi của nó. Thay thế số bằng một class mới

14. Replace Type Code with Subclasses 

Chúng ta có một code kiểu bất biến ảnh hưởng đến hành vi của một class. Thay thế code kiểu bằng các class con.

15. Replace Type Code with State/Strategy

Chúng ta có một code kiểu ảnh hưởng đến hành vi của một class, nhưng Chúng ta không thể sử dụng phân lớp. Thay thế loại code bằng một object trạng thái.

16. Replace Subclass with Fields

Chúng ta có các class con chỉ khác nhau trong mehtod trả về dữ liệu không đổi. Thay đổi các method thành các fields class cha và loại bỏ các class con

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>