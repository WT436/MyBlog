#### Cấu hình Mysql với docker

1. Cài đặt
* Tạo Docker network (Chia sẻ kết nối giữa các container)

    ``` docker
    docker network create mysql
    ```

* Tạo container từ image Mysql

    ``` docker
    docker run --name learn_mysql --network mysql -v /home/moe/mysql_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123 -d mysql:5.7
    ```
    trong đó:

    + --name learn_mysql: tên của container. Tên này sẽ được sử dụng ở bước sau, khi chúng ta khới tạo container chạy phpMyAdmin
    * --network mysql: đặt container này trong network mysql vừa được tạo ở bước 1
    * -v /home/moe/mysql_data:/var/lib/mysql : Volume dữ liệu từ container ra bên ngoài thư mục mysql_data mà chúng ta vừa tạo
    * -e MYSQL_ROOT_PASSWORD=123: đặt password cho user root. Mỗi một MySQL server khi được khởi tạo đều sẽ có một user root ban đầu.

    + Ví dụ : 
    ```
    docker
    docker run --name Wekee --network 76607ec725000d4a2ec62dc1966effb9626e7dc799898825e8da693c1443711a -v C:/mysql_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123 -d mysql:8.0
    or
    docker run --name hkcare -p 3316:3306 -v C:/mysql_data:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=123 -d mysql:8.0
    ```

    Đăng nhập : mysql Wb pass : 123, post : 3316,  host : 127.0.0.1 , userName : root
