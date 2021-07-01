# Giới thiệu về mô hình hoạt động TCP/IP

Mô hình TCP/IP (Transmission Control Protocol/ Internet Protocol - Giao thức điều khiển truyền nhận/ Giao thức liên mạng), là một bộ giao thức trao đổi thông tin được sử dụng để truyền tải và kết nối các thiết bị trong mạng internet. TCP/IP được phát triển để mạng được tin cậy hơn cùng với khả năng tự phục hồi tự động.

![image](https://user-images.githubusercontent.com/63473793/124133543-21ba0000-daac-11eb-8fe3-4abe70d400bb.png)

## Cách thức hoạt động của mô hình TCP/IP

Phân tích từ tên gọi, TCP/IP là sự kết hợp của 2 phương thức đó là IP (Giao thức liên mạng) cho phép các gói tin được gửi đến đích đã định sẵn, bằng các thêm các thông tin dẫn đường vào các gói tin được đến đúng đính định sẵn ban đầu. Và giao thức TCP(Giao thức truyền vận) đóng vai trò kiểm tra và đảm bảo sự an toàn cho cho mỗn gói tin khi đi qua mỗn trạm. TRong quá trình này, Nếu như giao thức TCP nhận thấy gói tin bị lỗi, Một tín hiệu sẽ yêu cầu hệ thống gửi lại một gói tin khác.

## Chắc năng của các tầng trong TCP/IP

Một mô hình tiêu chuẩn bao gồm 4 tầng được chồng lên nhau.

Tầng vật lý => Tầng mạng => Tầng giao vận => tầng ứng dụng

![image](https://user-images.githubusercontent.com/63473793/124134836-70b46500-daad-11eb-8ad2-a77557e07f07.png)

Tuy nhiên các chuyên gia cho rằng tầng Vật lý chia nhỏ ra thêm tầng Data Link 

1. Tầng 4 : Tầng ứng dụng 

![image](https://user-images.githubusercontent.com/63473793/124138220-a018a100-dab0-11eb-8aa9-21a72a8e13d9.png)

Đây là lớp giao diện trên cùng của mô hình. Đúng với tên gọi của nó . nó đảm nhiệm vai trò giao tiếp giữa 2 máy với nhau thông qua các dịch vụ mạng khác nhau dạng byte 

2. Tầng 3 : Tầng Giao vận

![image](https://user-images.githubusercontent.com/63473793/124138243-a6a71880-dab0-11eb-8b67-17d8424c4578.png)

Chức năng chính của tầng 3 là xử lý vấn đề giao tiếp giữa các máy chủ trong cùng một mạng hoặc khác mạng được kết nối với nhau thông qua bộ định tuyến.Tại đây dữ liệu sẽ được phân đoạn, mỗi đoạn sẽ không bằng nhau nhưng kích thước phải nhỏ hơn 64KB. Cấu trúc đầy đủ của một Segment lúc này là Header chứa thông tin điều khiển và sau đó là dữ liệu.

Trong tầng này còn bao gồm 2 giao thức cốt lõi là TCP và UDP. Trong đó, TCP đảm bảo chất lượng gói tin nhưng tiêu tốn thời gian khá lâu để kiểm tra đầy đủ thông tin từ thứ tự dữ liệu cho đến việc kiểm soát vấn đề tắc nghẽn lưu lượng dữ liệu. Trái với điều đó, UDP cho thấy tốc độ truyền tải nhanh hơn nhưng lại không đảm bảo được chất lượng dữ liệu được gửi đi.

3. Tầng 2 - Tầng mạng (Internet) 

![image](https://user-images.githubusercontent.com/63473793/124138573-f8e83980-dab0-11eb-8171-55bb49f05f69.png)

Tại đây, nó cũng được định nghĩa là một giao thức chịu trách nhiệm truyền tải dữ liệu một cách logic trong mạng. Các phân đoạn dữ liệu sẽ được đóng gói (Packets) với kích thước mỗi gói phù hợp với mạng chuyển mạch mà nó dùng để truyền dữ liệu. Lúc này, các gói tin được chèn thêm phần Header chứa thông tin của tầng mạng và tiếp tục được chuyển đến tầng tiếp theo. Các giao thức chính trong tầng là IP, ICMP và ARP.

Tầng 1 - Tầng Vật lý (Physical) 

Là sự kết hợp giữa tầng Vật lý và tầng liên kết dữ liệu của mô hình OSI. Chịu trách nhiệm truyền dữ liệu giữa hai thiết bị trong cùng một mạng. Tại đây, các gói dữ liệu được đóng vào khung (gọi là Frame) và được định tuyến đi đến đích đã được chỉ định ban đầu.