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