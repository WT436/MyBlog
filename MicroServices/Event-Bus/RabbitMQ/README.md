# RabbitMQ-EventBus-Extention

1. Giới thiệu về RabbitMQ
 
 - đầu tiên chúng ta cần hiểu lý do gì và tại sao một event bus hay Message broker, integration broker hoặc interface engine lại ra đời và tầm quan trọng của nó.

 ### Microservices Architecture
 
 ![image](https://user-images.githubusercontent.com/63473793/144191742-d6890e1c-f506-4ccb-abcd-5d439ffe1eb8.png)

Về cơ bản thì 1 cấu trúc micro nó la lá như vậy. các thành phần khác chúng ta sẽ không quan tâm. 
Trong kiến trúc cloud (hay microservices), các ứng dụng được chia thành những khối độc lập nhỏ hơn để có thể dễ dàng develop, deploy và maintain. Hãy thử tưởng tượng bạn có một kiến trúc cloud có nhiều service và nhiều request mỗi giây, bạn phải đảm bảo rằng không có bất cứ một request nào bị mất và web service của bạn luôn luôn sẵn sàng tiếp nhận request mới thay vì locked bởi đang xử lí request trước đó cũng như phải đảm bảo rằng các service giao tiếp với nhau một cách trơn tru và hiệu quả.

Vấn đề này đã sinh ra một thứ gọi là : Message Broker!

Message broker là một module trung gian trung chuyển message từ người gửi đến người nhận. Nó là một mô hình kiến trúc (architentural pattern) để kiểm tra, trung chuyển và điều hướng message; làm trung gian giữa các ứng dụng với nhau, tối giản hóa giao tiếp giữa các ứng dụng đó và để tăng hiệu quả tối đa cho việc tách ra các khối nhỏ hơn. Nhiệm vụ chính của một Message broker là tiếp nhận những message từ các ứng dụng và thực hiện một thao tác nào đó.

Có rất nhiều các MB khác nhau nhưng nổi tiếng và được ưa chuộng nhất có thể nói là : RabbitMQ

RabbitMQ là gì? RabbitMQ là một chương trình cho phép thực hiện việc trung chuyển tin nhắn, gọi là Message Broker nguồn mở. Đây cũng chính là chương trình đang được sử dụng rộng rãi khắp hiện nay trên toàn cầu. Người ta thu thập được thông tin đã có trên 35 ngàn lượt tải về và cài đặt chương trình này ở phạm vi toàn thế giới. RabbitMQ vì thế hiện hữu ở tất cả các doanh nghiệp từ quy mô nhỏ tới lớn.

Những hệ thống máy tính được áp dụng kiến trúc Microservice, tình trạng các service bị gọi chéo xảy ra rất nhiều gây ra tác hại khiến luồng xử lý trở nên phức tạp. Không chỉ vậy, các mức độ trao đổi dữ liệu của mọi thành phần trong hệ thống gia tăng làm cho hoạt động lập trình bị nhiễu loạn, nên cũng phức tạp hơn rất nhiều.

Thêm vào đó, mục tiêu của việc phát triển các ứng dụng đó chính là đảm bảo business và domain logic hơn. Các hệ thống có đặc điểm phân tán, do đó việc giao tiếp buộc phải có thêm điều kiện rằng chúng phải đồng điệu với nhau, tuy nhiên nó lại tác động không tốt cho việc các lập trình viên viết code.

RabbitMQ là một Message broker open-source, ban đầu được dùng cho Advanced Message Queuing Protocol (AMQP), sau đó đã được phát triển để hỗ trợ Streaming Text Oriented Messaging Protocol (STOMP), Message Queuing Telemetry Transport (MQTT), và những giao thức khác.RabbitMQ được viết bằng Erlang, một ngôn ngữ không phổ biến nhưng khá phù hợp với các công việc của Message Broker.

- Lợi ích :
  - Một nhà sản xuất không cần thiết phải biết khách hàng vì giờ dây với RabbitMQ, bạn chỉ cần gửi đi tin nhắn trong message broker. Phía khách hàng đăng ký nhận tin nhắn là có thể hoàn thành việc gửi và nhận dữ liệu trong thời gian rất ngắn.
  - Một nhà sản xuất sẽ giao tiếp với khách hàng qua chương trình trung gian này vậy cho nên nó giải quyết được các vấn đề bất đồng ngôn ngữ của cả hai bên. RabbitMQ hiện nay đã đưa ra tính năng hỗ trợ cho nhiều ngôn ngữ nên cuộc giao tiếp, trao đổi sẽ không gặp trở ngại.
  - Rabbit MQ có một đặc tính phổ biến đó là tính không đồng bộ. Producer sẽ không biết được lúc nào thì tin nhắn sẽ được gửi tới cho người dùng hoặc không rõ khi nào người dùng sẽ xử lý xong tin nhắn được gửi tới đó. Với producer thì nhiệm vụ của họ chỉ cần đẩy tin nhắn tới message broker, còn người dùng sẽ nhận tin nhắn nếu muốn. Đây là một đặc tính quan trọng để các lập trình viên xây dựng hệ thống lưu trữ, xử lý log.
  
2. Các thành phần chính - thuật ngữ chính cho messaging nói chúng và RabbitMQ nói riêng
  ### Producer   
  Một producer đẩy messages đến exchanges. Messages không được đẩy ở mức cao hơn mức mà Consumers có thể xử lý. Nó cũng chịu trách nhiệm tạo các routing keys.
    
  ### Exchange 
  Về cơ bản, nó là một  routing rule cho messages. Bây giờ, để một message đi đến một queue hoặc exchange khác với các producers, nó đòi hỏi phải có ràng buộc. Bây giờ các loại sàn giao dịch khác nhau yêu cầu các ràng buộc khác nhau. Một số exchanges là:
  - Fanout Exchange
    Nó định tuyến thông điệp đến tất cả các hàng đợi có sẵn mà không có sự phân biệt. Một khóa định tuyến, nếu được cung cấp, sẽ đơn giản bị bỏ qua. Trao đổi này rất hữu ích cho việc triển khai cơ chế pub-sub. Trong khi sử dụng trao đổi này, các hàng đợi khác nhau được phép xử lý các thông báo theo cách riêng của chúng, độc lập với những hàng khác.
  <br/>
  
   ![image](https://user-images.githubusercontent.com/63473793/144196535-99232e1b-d934-495e-b494-c34c54ef07c3.png)
  
    As shown in the diagram above, the messages are routed to all the queues.
  - Direct Exchange
    Nó định tuyến các thông điệp trên cơ sở khóa định tuyến mà thông điệp mang theo. Khóa định tuyến là một chuỗi ngắn được tạo bởi Nhà sản xuất thông báo. Các tin nhắn được chuyển đến các trao đổi / hàng đợi có Khóa liên kết khớp chính xác với khóa định tuyến.
   <br/>
  
   ![image](https://user-images.githubusercontent.com/63473793/144196695-d9cede17-bd4d-4a42-9228-82ef0b2f10f6.png)

   Như được minh họa trong sơ đồ trên, khóa định tuyến là “Apples” và các thông báo chỉ được gửi đến một hàng đợi có khóa ràng buộc là “Apples”
  - Topic Exchange
  Nó định tuyến các thông điệp trên cơ sở khớp hoàn toàn hoặc một phần với khóa định tuyến. Trong trường hợp này, các thông báo được xuất bản theo cách mà khóa định tuyến bao gồm các chuỗi từ được phân tách bằng dấu chấm (như word1.word2.word3). Các mẫu có thể có dấu hoa thị (*) có thể khớp với từ tại một vị trí nhất định của khóa định tuyến hoặc dấu băm có thể khớp với 0 hoặc nhiều từ.
   <br/>
  
   ![image](https://user-images.githubusercontent.com/63473793/144196828-1bb601c3-146e-42f3-9b5d-59c93669cade.png)

   Trong trường hợp trên, routing key là “Apples.Oranges.Lemons” và các tin nhắn được chuyển đến hai queues: Oranges và Apples
  - Headers exchange
  message được định tuyến dựa trên tiêu đề message. Các tiêu đề message được so khớp với các tiêu đề được chỉ định bởi hàng đợi ràng buộc và nếu khớp thì thư sẽ được gửi đến hàng đợi đó. Một đối số đặc biệt được gọi là "x-match" được thêm vào ràng buộc giữa một trao đổi và một hàng đợi. Bây giờ, giá trị này có thể có hai giá trị “bất kỳ” hoặc “tất cả”, trong đó “tất cả” là giá trị mặc định. "Tất cả" biểu thị rằng tất cả các cặp tiêu đề phải khớp, trong khi "bất kỳ" biểu thị rằng kết quả trùng khớp phải xảy ra với ít nhất một trong các cặp tiêu đề.
  <br/>
  
  ![image](https://user-images.githubusercontent.com/63473793/144199156-c6ed53e7-17d9-4aab-9b2f-bf1d89dd9654.png)

  Trong trường hợp trên, message được chuyển đến một hàng đợi mà “x-match” được đặt là “all” và tất cả các cặp key-value của nó (chỉ 1 trong trường hợp này) khớp với hàng đợi đó trong tiêu đề thư.

  - Consistent Hashing
 
  Loại trao đổi này băm khóa định tuyến hoặc tiêu đề thông báo để định tuyến các thông báo chỉ đến một hàng đợi. Điều này rất hữu ích trong những trường hợp chúng tôi phải đảm bảo rằng các tin nhắn được sử dụng theo thứ tự như đã xuất bản.
  
  ### Queue
  
   Nó là bộ đệm để lưu trữ tin nhắn. Hàng đợi được đặt tên để ứng dụng tham chiếu dễ dàng hơn. Các ứng dụng có thể quyết định tên hàng đợi hoặc có thể yêu cầu nhà môi giới tạo chúng. Tên hàng đợi có thể dài tới 255 byte ký tự UTF-8 và không được bắt đầu bằng ‘amq.’ Vì những tên như vậy được nhà môi giới dành riêng để sử dụng nội bộ. Hàng đợi được xác định bởi các thuộc tính sau: 
   - Tên 
   - Bền (Hàng đợi này có thể tồn tại sau khi khởi động lại nhà môi giới và đạt được bằng cách duy trì hàng đợi vào đĩa. Điều này không có nghĩa là các thông báo cũng lâu bền) 
   - Độc quyền (Chỉ được sử dụng bởi một kết nối và bị xóa sau khi kết nối đó đóng. Nếu bất kỳ kết nối nào khác cố gắng truy cập hàng đợi Dành riêng, nó sẽ ném ra một ngoại lệ cấp kênh có tên là RESOURCE_LOCKED) 
   - Tự động xóa (Hàng đợi sẽ tự động bị xóa khi người tiêu dùng cuối cùng đăng ký với nó hủy đăng ký) 
   - Đối số (Đây là tùy chọn; Hầu hết các đối số này có thể được thay đổi động ngay cả sau khi hàng đợi đã được khai báo. Chúng có thể được đặt theo hai cách: 
      - a) Đối với một nhóm hàng đợi bằng cách sử dụng các chính sách 
      - b) Trên cơ sở mỗi hàng đợi và các đối số được đặt khi khách hàng khai báo hàng đợi) 
   Trước khi sử dụng hàng đợi, nó cần được khai báo. Việc khai báo sẽ tạo ra một hàng đợi nếu nó chưa tồn tại. Bây giờ, trong trường hợp hàng đợi đã tồn tại, thì việc khai báo sẽ không có hiệu lực nếu các thuộc tính được chỉ định giống với thuộc tính hiện có, nếu không nó sẽ ném ra một ngoại lệ cấp kênh được gọi là PRECONDITION-FAILED.
  
  ### Consumer
  
  Nó đọc tin nhắn từ hàng đợi. Mỗi người tiêu dùng có thể đặt một thứ gọi là giới hạn tìm nạp trước (Hay còn gọi là giới hạn QoS). Con số này cho biết số lượng tin nhắn chưa được xác nhận mà Người tiêu dùng có thể xử lý tại một trường hợp.
  
3. Cầu hình căn bản

4. Xây dựng Extention cho .net core
