# Single Responsibility Principle

- Một class chỉ nên giữ 1 trách nhiệm duy nhất (Chỉ có thể sửa đổi class với 1 lý do duy nhất)

## Nghĩa là gì

- như một phần mình đã up , 1 class chỉ nên thực thi 1 chức năng duy nhất , 1 mà thôi
- như mình làm là cho 1 class học sinh nhé :
- có thể các bạn cx thấy 1 class thường các bạn viết nó có thông tin lưu trữ , rồi thì là nhập tên tuổi .... show tên tuổi ..... , ôi trời mẹ ơi nó nhỏ thì không sao chứ ví dụ bạn thử nhập class người xem , đi đứng nằm ngủ các kiểu con đà điểu . đang nghĩ thế cx đk mà , cho nó dễ đỡ phải tạo nhiều class đúng không
- rồi bây sở code mở rộng cực kỳ chi tiết về người thấy mẹ luôn lăn con chuột có mà thấy cụ nội luôn
- lúc đó kể cho con bé cùng phòng nghe nó chỉ chốt cho 1 câu "À thế ak , cụ đi chân lạnh toát nhé ", rồi khóc

- vậy thì chúng ta sẽ làm gì để giải quyết vấn đề này chia nó ra , nhớ kỹ 1 class chỉ 1 chức năng
- class đi là chỉ có đi thôi
- class lưu dữ liệu là chỉ lưu thôi ......
- tóm cái váy lại là ý để dễ maintain thì phải làm vậy (tương lai khóc hay cười tùy vào độ ngu của quá khứ ak nhầm độ lười của quá khứ)
