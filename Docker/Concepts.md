
# Concepts
Các khái niệm căn bản : 

Cấu trúc chung : 
<br/> ![image](https://user-images.githubusercontent.com/63473793/143561437-ae4e9387-1975-4ce8-8191-918972520f4f.png)

I. Các đối tượng thao tác - do docker quản lý

  1. Container 
  - Là một môi trường chạy run-time để chạy một ứng dụng độc lập. và vô cùng gọn nhẹ. chạy rất nhanh và quá y là dễ luôn.
  - Nó đảm bảo tính chính xác trong việc chạy trên nhiều môi trường khác nhau. và chia sẻ việc cài đặt này cho các máy khác nhau.
  - Nó chạy hoàn toàn đọc lập , và ít chịu ảnh hưởng bởi các container khác. cũng như server chạy trong nó.
  - Container chạy thì phải cần image và image thì ko
  - Khi 2 container bao bọc 2 application và mọi thứ cần thiết để chạy code kể cả file filesystem vậy  nên chúng sẽ tách biệt với nhau
  2. Image
  - Là một file bất biến - không thay đổi, chứa các source code, libraries, dependencies, tools và các files khác cần thiết cho một ứng dụng để chạy.
  - nó là một snapshot do tính chất chỉ đọc (read-only) mang trên nó.
  - Nó giúp cho phần mềm có thể chạy thử và test trong điều kiện ổn định của hẹ thống và thống nhất giữa các máy.
  - Nó không thể chạy hay start vì nó chỉ là các pattern nên nó được sử dụng làm cơ sở cho xây dựng   container. Giống kiểu class và interface vậy
  - Hãy hiểu nó như là một bản hợp đồng mẫu (interface) mà chưa có tính pháp lý thực thi (class) tức là mới chỉ trên giấy tờ chưa được thực thi.
  - Khi bạn tạo một container, nó sẽ thêm một lớp có thể ghi lên trên image bất biến, nghĩa là bây giờ bạn có thể sửa đổi nó.
  - ![image](https://user-images.githubusercontent.com/63473793/  143563670-8de02c7b-8542-4804-af87-b63ddeebac08.png)
  - Bản thân nó không thể sửa (cái này hơi khác chút với interface nhé).
  - Bạn có thể tạo số lượng Docker image không giới hạn từ một image base. Mỗi khi bạn thay đổi trạng  thái ban đầu của một image và lưu trạng thái hiện có, bạn tạo một image mới với một layer mới ở trên  nó. (giống commit của github) dạng tree
  - Docker file là chìa khóa để tạo ra 1 image và image lại là nền tảng để xây dựng len 1 container và container lại chính là nơi application chúng ta được dựng lên.
  -  ![image](https://user-images.githubusercontent.com/63473793/ 143565037-be107c74-7627-4080-a8aa-4debff806919.png)
  3. Network
  - Docker network sẽ đảm nhiệm nhiệm vụ kết nối mạng giữa các container với nhau, kết nối giữa   container với bên ngoài, cũng như kết nối giữa các cụm (swarm) docker containers.
  - alo alo container m nói cái j cơ , alo m có nghe thấy tao nói không alo
  - ![image](https://user-images.githubusercontent.com/63473793/  143583963-f7700c40-45a9-4d3e-b0fc-36ede6878d56.png)
  - Như đã nói ở trên thì container nó là đọc lập vậy nên muốn giao tiếp giữa chúng thì chúng ta cần đến một cuộc gọi là networking 
  - ![image](https://user-images.githubusercontent.com/63473793/  143584631-e96bad3c-4721-4796-a376-fb817a645167.png)
  - Sandbox : 
  - Endpoint : 
  - Network : 
  4. Data-volumes
  -  Là một volume được tạo ra cho phép các container mount volume vào trong các container hay dễ hiểu hơn là đocker sử dụng Volume đó thay thế cho 1 folder của container.
  -  Thằng này thì nó có thể tạo ra file.

II. Cấu trúc lõi từ ngoài vào trong của docker

  1. Client-docker-CLI
  - Là phương thức chính để người dùng thao tác với Docker. Khi người dùng gõ lệnh docker run namDepTrai <ví dụ như vạy đi :) > tức là người dùng sử dụng CLI và gửi request đến dockerd thông qua api, và sau đó Docker daemon sẽ xử lý tiếp.
  2. REST-API : nơi thực thi lắng nghe giữa CLI và daemon.
  3. Server-docker-daemon : server chạy ngầm phía dưới, là thành phần core, lắng nghe API request và quản lý các Docker object(image , container,....). Docker daemon host này cũng có thể giao tiếp được với Docker daemon ở host khác.

## Khác 
  1. Docker registry : là kho chưa image online ,nổi tiếng nhất chính là Docker Hub

Nhìn một cách tổng quan mà nói thì như sau : 

<br/> ![image](https://user-images.githubusercontent.com/63473793/143561108-425cae74-fd35-437f-9bab-684d9c137828.png)

- Client là nơi chúng ta sử dụng CLI để tương tác với daemon
- Từ daemon sẽ chỉ đạo Image
- Các Image sẽ được lưu trên docker Regitry 
- Các image trên docker_host (local) khi chạy sẽ tạo ra các container

Về cơ bản các khái niệm chính sẽ đến đây thôi. nếu nhớ được cái gì nữa sẽ update sau!