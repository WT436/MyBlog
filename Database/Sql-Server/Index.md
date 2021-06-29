# Đánh Index

Index được gọi là cấu trúc trong máy chủ SQL được duy trì hoặc lưu trữ trong cấu trúc trong bộ nhớ hoặc trên đĩa được liên kết với view hoặc table, được sử dụng chủ yếu để xác định bất kỳ hàng cụ thể nào hoặc tập hợp các hàng từ view hoặc table. Index trong SQL là các bảng tra cứu riêng lẻ, được sử dụng bởi công cụ tìm kiếm cơ sở dữ liệu để tăng tốc độ truy xuất dữ liệu tổng thể.

Một Index trong bảng được sử dụng để tăng tốc độ tổng thể cần thiết để tìm kiếm bất kỳ dữ liệu cụ thể nào trong cơ sở dữ liệu. Một Index trong cơ sở dữ liệu SQL có thể được sử dụng để xác định hiệu quả tất cả các hàng và một số cột phù hợp trong truy vấn và sau đó, người dùng có thể nhanh chóng nhập tập hợp con của bảng để xác định các kết quả phù hợp chính xác của câu hỏi được đề xuất.

SQL Index được sử dụng để nhanh chóng tìm dữ liệu trong bảng cơ sở dữ liệu mà không cần tìm kiếm từng hàng của nó. Trong SQL Index, bắt buộc phải duy trì nhiều không gian lưu trữ hơn để tạo bản sao cơ sở dữ liệu trùng lặp. Một Index lưu trữ dữ liệu đầy đủ trong bảng, được tổ chức hợp lý với các cột và hàng, được duy trì và lưu trữ vật lý trong dữ liệu theo hàng được gọi là kho lưu trữ hàng và trong trường hợp nếu bản ghi được lưu trữ trong dữ liệu theo cột, được gọi là Column store .

Nó bao gồm các kiểu như sau : 

## Clustered Index

### Giới thiệu

Các Clustered Index sắp xếp và lưu trữ dữ liệu hàng trong bảng hoặc view dựa trên các giá trị cơ bản của chúng. Có thể có trường hợp chỉ có một Index nhóm trong mỗi bảng, vì nó có thể cho phép người dùng lưu trữ dữ liệu theo một thứ tự Unique. Index thu thập lưu trữ dữ liệu theo cách được sắp xếp và do đó, bất cứ khi nào dữ liệu được chứa trong bảng theo cách được sắp xếp có nghĩa là nó được sắp xếp với Clustered Index.

Khi một bảng chứa một Clustered Index, nó được gọi là bảng được phân nhóm. Clustered Index được ưu tiên sử dụng khi cần sửa đổi dữ liệu khổng lồ trong bất kỳ cơ sở dữ liệu nào. Nếu dữ liệu được lưu trữ trong bảng hoặc cơ sở dữ liệu không được sắp xếp theo thứ tự tăng dần hoặc giảm dần, thì bảng dữ liệu được gọi là một đống hỗ độn.

Clustered Index được tổ chức thành các trang 8KB bằng cách sử dụng cấu trúc B-tree , để cho phép SQL Server Engine tìm các hàng được yêu cầu liên kết với các giá trị khóa index một cách nhanh chóng. Mỗi trang trong cấu trúc B-tree index được coi như một nút index. Nút cấp cao nhất được gọi là nút Gốc và các nút cấp dưới được gọi là nút Lá , nơi các trang dữ liệu bảng được lưu trữ và sắp xếp dựa trên các giá trị khóa index. Tất cả các nút nằm giữa nút gốc và nút lá được gọi là nút trung giancác nút mức. Tất cả các trang nằm ở cấp độ gốc và cấp độ trung gian chứa các giá trị khóa index đã được sắp xếp với một con trỏ đến nút cấp độ trung gian tiếp theo hoặc trang dữ liệu trong cấp độ lá index. Ngoài việc sắp xếp dữ liệu trong các trang index dựa trên các giá trị khóa của index, bản thân các trang sẽ được sắp xếp và liên kết trong một danh sách được liên kết kép trong index. Bất kỳ giá trị mới nào được chèn vào index đó sẽ tuân theo trình tự sắp xếp khóa index giữa các hàng hiện có.

![image](https://user-images.githubusercontent.com/63473793/123765508-00141980-d8f0-11eb-8e6d-43ddcf165ba3.png)

### Cân nhắc khi sử dụng

Các Clustered Index sẽ lợi cho các truy vấn mà cần đọc dữ liệu lớn và tuần tự.

Các đặc điểm lổi bật :

1. Short : Clustered Index rộng cũng sẽ ảnh hưởng đến tất cả các chỉ Non-Clustered Index được xây dựng trên Clustered Index đó, vì kClustered Index sẽ được sử dụng làm khóa tra cứu cho tất cả các Non-Clustered Index trỏ đến nó.

2. Static :Nên chọn các cột không bị thay đổi thường xuyên

3. Increasing :Sử dụng cột Increasing, chẳng hạn như cột IDENTITY, làm khóa chỉ mục được phân nhóm sẽ giúp cải thiện quy trình CHÈN, điều này sẽ chèn trực tiếp các giá trị mới vào cuối lôgic của bảng. Lựa chọn được đề xuất cao này sẽ giúp giảm dung lượng bộ nhớ cần thiết cho bộ đệm trang, giảm thiểu nhu cầu chia trang thành hai trang để phù hợp với các giá trị mới được chèn và sự xuất hiện phân mảnh, yêu cầu xây dựng lại hoặc tổ chức lại chỉ mục.

4. Unique :Nên khai báo cột khóa chỉ mục được nhóm hoặc kết hợp các cột là duy nhất để cải thiện hiệu suất truy vấn.

5. Accessed frequently :Điều này là do thực tế là các hàng sẽ được lưu trữ trong Clustered Index theo thứ tự được sắp xếp dựa trên key index đó được sử dụng để truy cập dữ liệu.

6. Order by: các hàng đã được sắp xếp dựa trên khóa chỉ mục được sử dụng trong mệnh đề ORDER BY.


### Các kiểu dữ liệu thích hợp cho Clustered Index

SMALLINT , INT và BIGINT là lựa chọn tốt nhất

Mặc dù GUID giá trị, được lưu trữ trong uniqueidentifier, thường được sử dụng như key clustered index, có một số thách thức mà đi kèm với thiết kế đó. Thách thức chính ảnh hưởng đến hiệu suất sắp xếp khóa chỉ mục theo cụm là bản chất của giá trị GUID lớn hơn các kiểu dữ liệu số nguyên, với kích thước 16 byte và nó được tạo theo cách ngẫu nhiên, khác với các giá trị số nguyên IDENTITY đang tăng liên tục. Kích thước lớn và sự tạo ngẫu nhiên của các giá trị GUID sẽ luôn dẫn đến các vấn đề tách trang và phân mảnh chỉ mục, điều này ảnh hưởng tiêu cực đến hiệu suất sử dụng chỉ mục theo nhóm.

Các kiểu dữ liệu CHAR cũng có thể được sử dụng, nhưng không được khuyến nghị.

Còn kiểu dữ liệu DATE không phải là duy nhất, nhưng nó có kích thước nhỏ và cung cấp hiệu suất sắp xếp tốt, đặc biệt đối với các truy vấn tìm kiếm phạm vi dữ liệu.

### Triển khai Clustered Index

Khi bạn tạo ràng buộc KHÓA CHÍNH trên một bảng, Clustered Index duy nhất sẽ được tạo tự động trên cột hoặc các cột tham gia vào ràng buộc đó để thực thi ràng buộc KHÓA CHÍNH, được đặt cùng tên với tên ràng buộc, trừ khi bạn đã xác định Clustered Index trên cùng một bảng. 

Vì vậy 1 bảng nên có 1 khóa chính và càng ít khóa ngoại càng tốt.

## Non-Clustered Index

Non-Clustered Index đặt ra một cấu trúc, được phân tách khỏi các hàng dữ liệu. Loại Index này trong SQL bao gồm các giá trị khóa Non-Clustered và mỗi cặp giá trị có một con trỏ đến hàng dữ liệu có tầm quan trọng thiết yếu. Trong Non-Clustered Index, mũi tên từ hàng Index đến hàng dữ liệu được gọi là bộ định vị hàng. Cấu trúc của bộ định vị hàng cho phép xác định xem các trang dữ liệu ở dạng bảng nhóm hay một đống. Trong biểu đồ phân cụm, bộ định vị hàng được gọi là khóa Index được phân nhóm.

Trong Non-Clustered Index, người dùng có thể dễ dàng thêm các cột không phải khóa vào cấp độ lá, vì nó bỏ qua các giới hạn khóa Index hiện có và thực hiện các truy vấn được lập Index đầy đủ. Một Non-Clustered Index được tạo ra để cải thiện hiệu suất tổng thể của các câu hỏi thường gặp, không nằm trong các mục được phân nhóm.

## Unique Index

Index Unique trong SQL đảm bảo và xác nhận rằng khóa Index không chứa bất kỳ giá trị trùng lặp nào và do đó, cho phép người dùng phân tích rằng mọi hàng trong bảng là Unique theo cách này hay cách khác. Index Unique của được sử dụng đặc biệt khi người dùng muốn có một đặc tính riêng của mỗi dữ liệu. Các Index Unique cho phép các cá nhân đảm bảo tính toàn vẹn dữ liệu của từng cột xác định của bảng trong cơ sở dữ liệu. Index này cũng cung cấp thông tin bổ sung về bảng dữ liệu, rất hữu ích cho trình tối ưu hóa truy vấn.

## Filtered Index

Index Filtered được tạo khi một cột chỉ có một số lượng nhỏ các giá trị có liên quan cho các truy vấn trên tập hợp con các giá trị. Trong trường hợp, khi một bảng bao gồm các hàng dữ liệu không đồng nhất, một Index Filtered sẽ được tạo trong SQL cho một hoặc nhiều loại dữ liệu. Ngay cả khi trình tối ưu hóa truy vấn không bao gồm bất kỳ truy vấn nào, nó vẫn chỉ ra một Index Filtered cho câu hỏi.

Index Filtered là một tính năng mới trong SQL và được sử dụng để lập Index một phần của các hàng trong bảng, có nghĩa là nó áp dụng bộ lọc trên Index và do đó, cải thiện hiệu suất tổng thể của truy vấn. Index Filtered dẫn đến việc khấu trừ chi phí duy trì Index và giảm chi phí lưu trữ Index so với Index toàn bảng. Tác động tổng thể của việc sửa đổi dữ liệu ít hơn với một Index đã lọc, vì nó chỉ được cập nhật khi một bản ghi mới được chèn vào hoặc khi dữ liệu của Index bị ảnh hưởng.

## Columnstore Index

Index Columnstore là một dạng tiêu chuẩn của Index khi nói đến việc lưu trữ và truy vấn các bảng dữ liệu kho dữ liệu lớn. Index Columnstore là một Index của SQL, được thiết kế để cải thiện hiệu suất của truy vấn trong trường hợp khối lượng công việc với lượng lớn dữ liệu. Loại Index này lưu trữ dữ liệu ở định dạng dựa trên cột. Index Columnstore làm giảm chi phí lưu trữ tổng thể và cung cấp mức nén rất cao đối với dữ liệu lớn. Do việc nén dữ liệu được lưu trữ, người dùng có thể thực hiện các chức năng đầu vào - đầu ra một cách hiệu quả và do đó, mang lại hiệu suất cao.

Index Columnstore cho phép lưu trữ dữ liệu trong phạm vi nhỏ, giúp tăng tốc độ xử lý. Việc sử dụng Index này cho phép người dùng nhận được IO với hiệu suất truy vấn cao hơn 10 lần so với lưu trữ hướng hàng truyền thống. Đối với phân tích, Columnstore Index cung cấp thứ tự độ lớn để có hiệu suất tốt hơn các Index khác trong SQL. Giá trị Index Columnstore từ cùng một miền có giá trị tương tự, điều này làm tăng tốc độ nén dữ liệu tổng thể.

## Hash Index

Hash Index trong SQL chỉ đơn giản là một mảng gồm N nhóm hoặc vị trí chứa một con trỏ và một hàng trên mỗi nhóm hoặc vị trí. Index băm sử dụng hàm băm F (K, N), trong đó K là quan trọng và số nhóm là N. Hàm ánh xạ ra khóa tương ứng với nhóm của chỉ số băm. Mỗi nhóm của Index băm bao gồm 8 byte, được sử dụng để lưu trữ địa chỉ bộ nhớ của danh sách liên kết các mục nhập quan trọng.

Thật ra Tôi vẫn chưa thông thạo 7 cái món index này cho lắm. Một số thành phần vẫn còn bỡ ngỡ. nhưng rất nhanh thôi! Sau ngày hôm nay sẽ có bản vá cho phần này sẽ thông thạo 7. sau 2 -3 ngày thôi!

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>