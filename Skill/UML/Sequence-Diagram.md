# Sequence Diagram
## What?

Sequence Diagram là một dạng sơ đồ tương tác hiển thị các đối tượng dưới dạng huyết mạch chạy xuống trang, với các tương tác của chúng theo thời gian được biểu thị dưới dạng thông báo được vẽ dưới dạng mũi tên từ huyết mạch nguồn đến huyết mạch mục tiêu.

Sequence Diagram rất tốt trong việc chỉ ra đối tượng nào giao tiếp với đối tượng nào khác; và những thông điệp nào kích hoạt những liên lạc đó. Biểu đồ trình tự không nhằm mục đích hiển thị logic thủ tục phức tạp.


I. Lifelines

đại diện cho một người tham gia cá nhân trong một sơ đồ tuần tự. Một Lifelines thường sẽ có một hình chữ nhật chứa tên đối tượng của nó. Nếu tên của nó là "self", điều đó chỉ ra rằng Lifelines đại diện cho bộ phân loại sở hữu sơ đồ trình tự.

![image](https://user-images.githubusercontent.com/63473793/123454137-6d7f2c00-d60a-11eb-8ad3-da89a0045764.png)

Đôi khi một sơ đồ trình tự sẽ có một Lifelines với một biểu tượng phần tử tác nhân ở đầu của nó. Điều này thường xảy ra nếu sơ đồ tuần tự thuộc sở hữu của một ca sử dụng. Các yếu tố ranh giới, kiểm soát và thực thể từ biểu đồ độ mạnh cũng có thể sở hữu các đường sống.

![image](https://user-images.githubusercontent.com/63473793/123454323-a15a5180-d60a-11eb-9cc3-74ecd41fdd33.png)

II. Messages

Messages được hiển thị dưới dạng mũi tên. Messages có thể hoàn chỉnh, bị mất hoặc được tìm thấy; đồng bộ hoặc không đồng bộ; cuộc gọi hoặc tín hiệu. Trong sơ đồ sau, thông báo đầu tiên là một thông báo đồng bộ (được biểu thị bằng đầu mũi tên liền khối) hoàn chỉnh với một thông báo trả về ngầm định; thông báo thứ hai là không đồng bộ (được biểu thị bằng đầu mũi tên dòng) và thông báo thứ ba là thông báo trả về không đồng bộ (biểu thị bằng đường đứt nét).

![image](https://user-images.githubusercontent.com/63473793/123454401-b6cf7b80-d60a-11eb-8e5e-f19aab8880c0.png)

III. Execution Occurrence

Một hình chữ nhật mỏng chạy dọc theo Lifelines biểu thị sự xuất hiện thực thi hoặc kích hoạt tiêu điểm điều khiển. Trong sơ đồ trước, có ba lần thực thi. 
* Đầu tiên là đối tượng nguồn gửi hai tin nhắn và nhận được hai hồi đáp; 
* Thứ hai là đối tượng đích nhận một thông điệp đồng bộ và gửi trả lời; 
* Thứ ba là đối tượng đích nhận một thông điệp không đồng bộ và gửi trả lời.

IV. Self Message

Một thông điệp tự có thể đại diện cho một cuộc gọi đệ quy của một hoạt động hoặc một phương thức gọi một phương thức khác thuộc cùng một đối tượng. Nó được hiển thị như là tạo ra một trọng tâm kiểm soát lồng vào nhau trong quá trình thực thi của Lifelines.

![image](https://user-images.githubusercontent.com/63473793/123454895-407f4900-d60b-11eb-9120-ae54f76edc50.png)

V. Lost and Found Messages

là những thư được gửi đi nhưng không đến người nhận dự kiến hoặc đến người nhận không được hiển thị trên sơ đồ hiện tại. Messages được tìm thấy là những thư đến từ một người gửi không xác định hoặc từ một người gửi không được hiển thị trên sơ đồ hiện tại. Chúng được biểu thị là đi đến hoặc đến từ một phần tử điểm cuối.

![image](https://user-images.githubusercontent.com/63473793/123455073-7cb2a980-d60b-11eb-8595-5f143aa03fa1.png)

VI. Lifeline Start and End

Một Lifeline có thể được tạo ra hoặc bị phá hủy trong khoảng thời gian được biểu thị bằng biểu đồ tuần tự. Trong trường hợp thứ hai, Lifeline được kết thúc bằng một biểu tượng dừng, được biểu thị dưới dạng một cây thánh giá. Trong trường hợp trước đây, biểu tượng ở đầu Lifeline được hiển thị ở cấp độ thấp hơn dưới trang so với biểu tượng của đối tượng đã gây ra sự sáng tạo. Biểu đồ sau đây cho thấy một đối tượng đang được tạo và phá hủy.

![image](https://user-images.githubusercontent.com/63473793/123455086-80463080-d60b-11eb-8890-8a23e4934b03.png)

VII. Duration and Time Constraints

Theo mặc định, một thông báo được hiển thị dưới dạng một đường ngang. Vì đường huyết mạch đại diện cho thời gian trôi qua trên màn hình, khi lập mô hình hệ thống thời gian thực hoặc thậm chí là quy trình kinh doanh có giới hạn thời gian, điều quan trọng là phải xem xét khoảng thời gian cần thiết để thực hiện các hành động. Bằng cách đặt giới hạn thời lượng cho một tin nhắn, tin nhắn sẽ được hiển thị dưới dạng một đường dốc.

![image](https://user-images.githubusercontent.com/63473793/123455193-a075ef80-d60b-11eb-9b95-1a3887e6f32a.png)

VIII. Combined Fragments

Trước đó, người ta đã nói rằng sơ đồ trình tự không nhằm mục đích hiển thị logic thủ tục phức tạp. Trong trường hợp này, có một số cơ chế cho phép thêm một mức độ logic thủ tục vào sơ đồ và nằm dưới tiêu đề của các đoạn kết hợp. Một phân đoạn kết hợp là một hoặc nhiều trình tự xử lý nằm trong một khung và được thực thi trong các trường hợp được đặt tên cụ thể. Các đoạn có sẵn là:
  * Các mô hình phân mảnh thay thế (được ký hiệu là “alt”) nếu… then… cấu tạo khác.
  * Cấu trúc chuyển đổi mô hình phân đoạn tùy chọn (được ký hiệu là “opt”).
  * Phân đoạn ngắt mô hình một chuỗi sự kiện thay thế được xử lý thay vì toàn bộ phần còn lại của sơ đồ.
  * Phân đoạn song song (ký hiệu là “par”) mô hình xử lý đồng thời.
  * Phân đoạn trình tự yếu (được ký hiệu là “seq”) bao gồm một số trình tự mà tất cả các thông báo phải được xử lý trong phân đoạn trước trước khi phân đoạn sau có thể bắt đầu, nhưng không áp đặt bất kỳ trình tự nào trong phân đoạn đối với các thông báo không chia sẻ một dây cứu sinh.
  * Phân đoạn trình tự nghiêm ngặt (được ký hiệu là "nghiêm ngặt") bao gồm một loạt các thông báo phải được xử lý theo thứ tự nhất định.
  * Phân đoạn phủ định (được ký hiệu là "neg") bao gồm một chuỗi thông báo không hợp lệ.
  * Đoạn quan trọng bao quanh một đoạn quan trọng.
  * Phân đoạn bỏ qua tuyên bố một thông báo hoặc thông báo không được quan tâm nếu nó xuất hiện trong ngữ cảnh hiện tại.
  * Phân đoạn xem xét có hiệu lực ngược lại với phân đoạn bỏ qua: bất kỳ thông báo nào không có trong phân đoạn xem xét sẽ bị bỏ qua.
  * Phân đoạn xác nhận (được ký hiệu là “khẳng định”) chỉ định rằng bất kỳ chuỗi nào không được hiển thị dưới dạng toán hạng của khẳng định đều không hợp lệ.
  * Phân đoạn vòng lặp bao gồm một loạt các thông báo được lặp lại.
Sơ đồ sau đây cho thấy một đoạn vòng lặp.

![image](https://user-images.githubusercontent.com/63473793/123455285-b84d7380-d60b-11eb-8496-7ffb87c98714.png)

Ngoài ra còn có một sự tương tác xảy ra, tương tự như một đoạn kết hợp. Sự xuất hiện tương tác là một tham chiếu đến một sơ đồ khác có từ "ref" ở góc trên cùng bên trái của khung và có tên của sơ đồ được tham chiếu được hiển thị ở giữa khung.

IX. Gate

Gate là một điểm kết nối để kết nối một thông điệp bên trong một đoạn với một thông điệp bên ngoài một đoạn. EA hiển thị một cổng như một hình vuông nhỏ trên một khung phân mảnh. Gate sơ đồ hoạt động như các đầu nối ngoài trang cho sơ đồ trình tự, đại diện cho nguồn của các thông điệp đến hoặc mục tiêu của các thông điệp đi. Hai sơ đồ sau đây cho thấy cách chúng có thể được sử dụng trong thực tế. Lưu ý rằng Gate trên sơ đồ cấp cao nhất là điểm tại đó đầu mũi tên thông báo chạm vào đoạn tham chiếu - không cần phải hiển thị nó dưới dạng hình hộp.

![image](https://user-images.githubusercontent.com/63473793/123455385-d61ad880-d60b-11eb-93c1-ef095027e64b.png)

![image](https://user-images.githubusercontent.com/63473793/123455393-d915c900-d60b-11eb-8836-a701e0297607.png)

X. Part Decomposition

Một đối tượng có thể có nhiều hơn một Lifeline đến từ nó. Điều này cho phép các thông báo nội bộ và nội bộ được hiển thị trên cùng một sơ đồ.

![image](https://user-images.githubusercontent.com/63473793/123455624-1f6b2800-d60c-11eb-928b-2af1d16595e4.png)

XI. State Invariant / Continuations

State Invariant là một ràng buộc được đặt trên một Lifeline phải đúng tại thời điểm chạy. Nó được hiển thị như một hình chữ nhật với các đầu là hình bán nguyệt.

![image](https://user-images.githubusercontent.com/63473793/123455647-27c36300-d60c-11eb-823e-44c68c40f63c.png)

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>