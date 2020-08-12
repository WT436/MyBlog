# Observer Pattern

1. Định Nghĩa:  Observer là một mẫu thiết kế hành vi cho phép bạn xác định cơ chế đăng ký để thông báo cho nhiều đối tượng về bất kỳ sự kiện nào xảy ra với đối tượng mà họ đang quan sát.
-  Tại sao nó lại là người quan sát : hiểu nôm na là ntn , giống như trong một  buổi phỏng vấn , người phỏng vấn sẽ đặt ra câu hỏi đúng không , ok vậy người phỏng vấn chính là người quan sát chúng ta . chúng ta người trả lời phỏng vấn chính là người sẽ giải đáp cái thắc mắc đó . nếu như các bạn đang tưởng tưởng 1 vs 1 thì nó cx đúng nhưng hãy mở rộng ra nào , vd như bạn là bill gates chẳng hạn , bạn đến 1 buổi thuyết trình triệu người xem , vậy triệu người xem đó chính là người theo dõi bạn , Bạn nói tôi đã có win 10 xịn xò  chẳng hạn , ngay lập tức , 1 triệu người đang theo dõi bạn sẽ nhận được 1 lời mời setting win 10  sớm nhất , 
![observer](https://user-images.githubusercontent.com/63473793/90074489-8f8afb00-dd25-11ea-873c-b735ec43a368.png)
2. Vấn Đề :  Hãy tưởng tượng rằng bạn có hai loại đối tượng: Khách hàng và Cửa hàng. Khách hàng rất quan tâm đến một thương hiệu sản phẩm cụ thể (giả sử đó là một mẫu iPhone mới) sẽ sớm có mặt trong cửa hàng.
-  Vấn đề đặt ra ở đây là , để giữ được khách hàng , hay nói cách khác là để  khách hàng có thể biết được thông tin mà chúng ta mới cập nhật , thì  chính khách hàng không thể ngày hôm nay đến của hàng để xem Win 10   mới đã lên kệ hay chưa ....
- Cái tiếp theo , chắc hẳng các bạn sẽ nghĩ là ồ vậy ta sẽ gửi mail cho từng khách đúng không , vậy họ đăng ký ở đâu , như thế nào ,  cách giải quyết ra sao , thay vì tạo ra 1 đống bùi nhùi class để sử lý vấn đề này .
-  khách hàng lãng phí thời gian kiểm tra sản phẩm còn hàng hoặc cửa hàng lãng phí nguồn lực để thông báo sai cho khách hàng.
-  Khi các bạn có thể code cách thông thường  tôi cam đoan code sẽ sảy ra  xung đột. 

3. Cấu trúc 