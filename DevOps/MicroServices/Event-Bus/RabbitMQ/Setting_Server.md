### Cấu hình RabbitMQ

Tạo 1 file : docker-compose.yaml

``` yaml

version: "3.8"
services:
  rabbitmq3:
    image: rabbitmq:3.8-management-alpine
    container_name: "rabbitmq"       
    environment:
        - RABBITMQ_DEFAULT_USER= WT436
        - RABBITMQ_DEFAULT_PASS= WT436
    ports:
        # AMQP protocol port
        - '5672:5672'
        # HTTP management UI
        - '15672:15672'
    volumes:
        - C:/logs/rabbitmq/data/:/var/lib/rabbitmq/
        - C:/logs/rabbitmq/log/:/var/log/rabbitmq
    networks:
        - rabbitmq_go_net

networks:
  rabbitmq_go_net:
    driver: bridge
    
```
- Khởi động docker. di chuyển cmd về folder chứa file docker-compose.yaml

- Run lệnh : docker-compose up để cài đặt và chạy rabbit

- 

![image](https://user-images.githubusercontent.com/63473793/123521965-4432ce80-d6e4-11eb-9ec8-22a38c443ccf.png)