# Activity Diagram
## What?

Activity diagram được sử dụng để hiển thị chuỗi các hoạt động.hiển thị quy trình làm việc từ điểm bắt đầu đến điểm kết thúc chi tiết nhiều đường dẫn quyết định tồn tại trong tiến trình của các sự kiện có trong hoạt động.
Chúng có thể được sử dụng để trình bày chi tiết các tình huống mà quá trình xử lý song song có thể xảy ra trong quá trình thực hiện một số hoạt động.

## Ví dụ

![image](https://user-images.githubusercontent.com/63473793/123426611-d0ae9580-d5ed-11eb-8e9c-1152cc234862.png)

## Chú giải

1. Activities 

![image](https://user-images.githubusercontent.com/63473793/123432849-0440ee00-d5f5-11eb-83b2-f0fe5ac45d08.png)

Activities là đặc tả của một chuỗi hành vi được tham số hóa. Hoạt động được hiển thị dưới dạng hình chữ nhật có góc tròn bao quanh tất cả các hành động, luồng kiểm soát và các yếu tố khác tạo nên hoạt động.

2. Actions

![image](https://user-images.githubusercontent.com/63473793/123442430-12940780-d5ff-11eb-9ab7-c7e2db9d30a2.png)

đại diện cho một bước duy nhất trong một hoạt động. Các thao tác được biểu thị bằng các hình chữ nhật có góc tròn.

3. Action Constraints

![image](https://user-images.githubusercontent.com/63473793/123442570-35262080-d5ff-11eb-98ca-bef47d7d7b32.png)

Các ràng buộc có thể được gắn vào một hành động. Biểu đồ sau đây cho thấy một hành động với các điều kiện trước và sau cục bộ.

4. Control Flow

![image](https://user-images.githubusercontent.com/63473793/123442677-5424b280-d5ff-11eb-9a51-e36c76e10c1e.png)

Luồng kiểm soát hiển thị luồng kiểm soát từ hành động này sang hành động tiếp theo. Kí hiệu của nó là một đường có đầu mũi tên.

5. Initial Node

![image](https://user-images.githubusercontent.com/63473793/123442792-74547180-d5ff-11eb-840a-842e9e2f64c4.png)
Một nút ban đầu hoặc nút bắt đầu được mô tả bằng một điểm đen lớn, như được hiển thị bên dưới. 

6. Final Node

![image](https://user-images.githubusercontent.com/63473793/123442921-9817b780-d5ff-11eb-9830-1914461272ef.png)

![image](https://user-images.githubusercontent.com/63473793/123442982-a6fe6a00-d5ff-11eb-865d-62f73a164123.png)

Có hai loại nút cuối cùng: nút hoạt động và nút cuối cùng của luồng. Nút cuối cùng của hoạt động được mô tả như một vòng tròn với một dấu chấm bên trong.

7. Objects and Object Flows

![image](https://user-images.githubusercontent.com/63473793/123443116-cb5a4680-d5ff-11eb-8fc9-a860d15ac688.png)

Luồng đối tượng là một đường dẫn mà các đối tượng hoặc dữ liệu có thể đi qua. Một đối tượng được hiển thị dưới dạng hình chữ nhật.

![image](https://user-images.githubusercontent.com/63473793/123443199-e1680700-d5ff-11eb-9300-6abdd7927b2f.png)

Luồng đối tượng được hiển thị dưới dạng đầu nối có đầu mũi tên biểu thị hướng đối tượng đang được truyền qua.

![image](https://user-images.githubusercontent.com/63473793/123443283-f80e5e00-d5ff-11eb-8d98-5698b51382c9.png)

Một luồng đối tượng phải có một đối tượng ở ít nhất một trong các đầu của nó. Một ký hiệu viết tắt cho sơ đồ trên sẽ là sử dụng các chân đầu vào và đầu ra.

![image](https://user-images.githubusercontent.com/63473793/123443337-02c8f300-d600-11eb-877e-dbd9d7c3fafe.png)

Kho dữ liệu được hiển thị dưới dạng một đối tượng với từ khóa «kho dữ liệu».

8. Decision and Merge Nodes

![image](https://user-images.githubusercontent.com/63473793/123443394-11170f00-d600-11eb-9b8e-615739b1c98a.png)

Các nút quyết định và các nút hợp nhất có cùng ký hiệu: hình thoi. Cả hai đều có thể được đặt tên. Các luồng điều khiển đến từ một nút quyết định sẽ có các điều kiện bảo vệ cho phép luồng điều khiển chạy nếu điều kiện bảo vệ được đáp ứng. Sơ đồ sau đây cho thấy việc sử dụng một nút quyết định và một nút hợp nhất.

9. Fork and Join Nodes

![image](https://user-images.githubusercontent.com/63473793/123443518-2ab85680-d600-11eb-9e51-a5e52b35e707.png)

có cùng ký hiệu: thanh ngang hoặc thanh dọc (hướng phụ thuộc vào việc luồng điều khiển chạy từ trái sang phải hay từ trên xuống dưới). Chúng chỉ ra điểm bắt đầu và kết thúc của các luồng điều khiển đồng thời. Sơ đồ sau đây cho thấy một ví dụ về việc sử dụng chúng.

10. Expansion Region

là một vùng hoạt động có cấu trúc thực thi nhiều lần. Các nút mở rộng đầu vào và đầu ra được vẽ dưới dạng một nhóm ba hộp đại diện cho nhiều lựa chọn mục. Từ khóa "lặp đi lặp lại", "song song" hoặc "luồng" được hiển thị ở góc trên cùng bên trái của vùng.

![image](https://user-images.githubusercontent.com/63473793/123443586-3ad03600-d600-11eb-8184-e0c029b5d81e.png)

11. Exception Handlers

Các trình xử lý ngoại lệ có thể được mô hình hóa trên sơ đồ hoạt động như trong ví dụ bên dưới.

![image](https://user-images.githubusercontent.com/63473793/123443643-4885bb80-d600-11eb-8899-e65770f0e28f.png)

12. Interruptible Activity Region

Một vùng hoạt động có thể bị gián đoạn bao quanh một nhóm các hành động có thể bị gián đoạn. Trong ví dụ rất đơn giản dưới đây, hành động "Lệnh xử lý" sẽ thực thi cho đến khi hoàn thành, khi đó nó sẽ chuyển quyền kiểm soát cho hành động "Đóng lệnh", trừ khi nhận được ngắt "Yêu cầu hủy", hành động này sẽ chuyển quyền kiểm soát cho "Lệnh hủy " hoạt động.

![image](https://user-images.githubusercontent.com/63473793/123443697-550a1400-d600-11eb-9bc4-543081f29152.png)

13. Partition

Phân vùng hoạt động được hiển thị dưới dạng một tấm bơi ngang hoặc dọc. Trong sơ đồ sau, các phân vùng được sử dụng để tách các hành động trong một hoạt động thành các hoạt động do bộ phận kế toán thực hiện và các hoạt động do khách hàng thực hiện.

![image](https://user-images.githubusercontent.com/63473793/123443756-64895d00-d600-11eb-9fc6-cf69d5e44155.png)


 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>