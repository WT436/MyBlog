# Composing Methods

Phần lớn việc tái cấu trúc được dành cho các phương pháp soạn thảo chính xác. Trong hầu hết các trường hợp, các phương pháp dài quá mức là gốc rễ của mọi điều ác. Sự mơ hồ của code bên trong các method này che giấu logic thực thi và làm cho method cực kỳ khó hiểu - và thậm chí còn khó thay đổi hơn.

Các kỹ thuật tái cấu trúc trong nhóm này hợp lý hóa các phương pháp, loại bỏ sự trùng lặp code và mở đường cho những cải tiến trong tương lai.

1. Extract Method

Bạn có một đoạn mã có thể được nhóm lại với nhau. Biến đoạn này thành một phương thức có tên giải thích mục đích của phương thức này

2. Inline Method

Nội dung của một phương thức cũng rõ ràng như tên của nó. Đặt nội dung của phương thức vào phần nội dung của người gọi và xóa phương thức.

3. Extract Variable
4. Inline Temp

Bạn có một tạm thời được gán cho một lần với một biểu thức đơn giản, và tạm thời đang cản trở các phép tái cấu trúc khác. Thay thế tất cả các tham chiếu đến tạm thời đó bằng biểu thức.

5. Replace Temp with Query

Bạn đang sử dụng một biến tạm thời để giữ kết quả của một biểu thức. Trích xuất biểu thức thành một phương thức. Thay thế tất cả các tham chiếu đến tạm thời bằng biểu thức. Phương pháp mới sau đó có thể được sử dụng trong các phương pháp khác.

6. Introduce Explaining Variable 

Bạn có một biểu hiện phức tạp. Đặt kết quả của biểu thức hoặc các phần của biểu thức vào một biến tạm thời có tên giải thích mục đích.

7. Split Temporary Variable

Bạn có một biến tạm thời được gán cho nhiều lần, nhưng không phải là biến vòng lặp cũng không phải là biến tạm thời thu thập. Tạo một biến tạm thời riêng biệt cho mỗi nhiệm vụ.

8. Remove Assignments to Parameters

Mã gán cho một tham số. Sử dụng một biến tạm thời để thay thế. Được thúc đẩy bởi thao tác có thể không được quan sát do những thay đổi được thực hiện đối với đối tượng mà một tham chiếu trỏ đến.

9. Replace Method With Method Object

Bạn có một phương thức dài sử dụng các biến cục bộ theo cách mà bạn không thể áp dụng Phương pháp trích xuất. Biến phương thức thành đối tượng của chính nó để tất cả các biến cục bộ trở thành trường trên đối tượng đó. Sau đó, bạn có thể phân tách phương thức thành các phương thức khác trên cùng một đối tượng.

10. Substitute Algorithm

Bạn muốn thay thế một thuật toán bằng một thuật toán rõ ràng hơn. Thay thế phần thân của phương thức bằng thuật toán mới.

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>