### Thuật ngữ và cách dùng với RabbitMQ UI

1. Exchanges

- Trong RabbitMQ, Một producer không bao giờ gửi tin nhắn trực tiếp đến queue. Thay vào đó, nó sử dụng một Exchanges làm trung gian định tuyến.

- Do đó, Exchanges sẽ quyết định xem thông báo có được chuyển đến một queue, đến nhiều queue hay chỉ đơn giản là bị loại bỏ.

- Ví dụ: tùy thuộc vào chiến lược định tuyến, chúng tôi có bốn loại Exchanges để lựa chọn:
    + Type : 
        - Direct  : Trao đổi chuyển tiếp tin nhắn đến hàng đợi dựa trên khóa định tuyến.
        - Fanout : Trao đổi bỏ qua khóa định tuyến và chuyển tiếp thông báo đến tất cả các hàng đợi bị ràng buộc.
        - Topic : Trao đổi định tuyến thông điệp đến các hàng đợi có giới hạn bằng cách sử dụng kết hợp giữa một mẫu được xác định trên trao đổi và các khóa định tuyến được gắn vào hàng đợi.
        - Headers : Trong trường hợp này, các thuộc tính tiêu đề thư được sử dụng, thay vì khóa định tuyến, để liên kết trao đổi với một hoặc nhiều hàng đợi.
    
    + Name : Tên của Exchanges.
    + Durability  : nếu enabled, Exchanges sẽ không xóa sàn giao dịch trong trường hợp khởi động lại.
    + Auto-Delete : khi tùy chọn này được bật, nhà môi giới sẽ xóa sàn giao dịch nếu nó không bị ràng buộc vào hàng đợi.

    + Optional arguments : Đối số tùy chọn để khai báo trong code.
    ```c#
    Map<String, Object> exchangeArguments = new HashMap<>();
    exchangeArguments.put("alternate-exchange", "orders-alternate-exchange");

    channel.exchangeDeclare("orders-direct-exchange", BuiltinExchangeType.DIRECT, true, false, exchangeArguments);
    ```

2. Queues

- Tương tự như các nhà môi giới nhắn tin khác, Queues RabbitMQ gửi tin nhắn đến người tiêu dùng dựa trên mô hình FIFO.

- Properties Queues : 
    + Name : Tên định danh của Queues.
    + Durability  : Nếu enabled ,broker sẽ không xóa Queues trong trường hợp khởi động lại.
    + Exclusive : Nếu enabled Queues sẽ chỉ được sử dụng bởi một kết nối và sẽ bị xóa khi kết nối bị đóng.
    + Auto-delete : Nếu enabled, broker xóa Queues khi người tiêu dùng cuối cùng hủy đăng ký.
    + Optional arguments : 
        ``` c# 
        Map<String, Object> queueArguments = new HashMap<>();
        queueArguments.put("x-message-ttl", 60000);
        queueArguments.put("x-max-priority", 10);

        channel.queueDeclare("orders-queue", true, false, false, queueArguments);
        ```

3. Bindings 

- Exchanges sử dụng các ràng buộc để định tuyến thông báo đến các Queues cụ thể. Đôi khi, chúng có một khóa định tuyến gắn liền với chúng, được một số loại Exchanges sử dụng để lọc các thông điệp cụ thể và định tuyến chúng đến Queues bị ràng buộc. Cuối cùng, hãy liên kết Queues mà chúng ta đã tạo với Exchanges bằng cách sử dụng khóa định tuyến:

```c# 
channel.queueBind("orders-queue", "orders-direct-exchange", "orders-routing-key");
```