# Refactoring techniques

Refactoring là một quá trình cải tiến code có thể kiểm soát được mà không tạo ra chức năng mới. Nó biến những thứ hỗn độn thành những thiết kế đơn giản hơn và clean code.

Khi đọc đến đây tôi thành thật khuyên bạn dừng lại. Và quay lại đọc và áp dụng Clean code thành thói quen trước.Con đường dài bao giờ cũng cần những bước chân nhỏ bé và vững chắc. Nếu đã từng đọc 'Code lởm' thì bạn mới thấy tầm quan trọng của Clean code nó là như thế nào. Nó không thể tả không thể viết chỉ là cảm giác của một người không còn chút tâm trí nào để vào việc. Tôi không bao giờ chấp nhận việc code vô tội vạ. Code không có nguyên tắc!

Dưới đây là một vài ưu điểm của nó :

* Tạo ra sự minh bạch , rõ ràng cho các lập trình viêc khác đọc code của bạn.
* Code không bị lặp đi lặp lại (Cấm copy paste thành thói quen) việc thay đổi phần code đó có thể dẫn đến các đoạn code khác cũng phải sửa theo
* Code được clean thì bao giờ cũng ít hơn , sạch hơn , dễ nhớ hơn, dễ bảo trì hơn, ít bug hơn ,ngắn hơn và đơn giản hơn.
* Dễ dàng test và pass test hơn. (Tester sẽ nhàn hơn. trẻ trung hơn , xinh đẹp hơn trong mắt Devs!)
* ........... kể có đến múc cả bể chửa xong!

Và sau khi đã ngấm Clean code đến mức đọc 'code lởm' là méo muốn là việc nữa thì đã đến lúc thay đổi cả nhưng thứ đã quá là kinh khủng đó. Lúc này chính là lúc mà Refactoring techniques phát huy tài năng và sức ảnh hưởng của nó. 

Chào mừng đến với Refactoring techniques. Nơi mà 'Code lởm' Không có chỗ đứng!

## Menu 

I. Composing Methods
II. Moving Features Between Objects
III. Organisation Data
IV. Simplifying Conditional Expressions
V. Making Method Calls Simpler
VI. Dealing with Generalisation
VII. Big Refactoring
VIII. Signs of code that might need refactoring

> Sơ bộ các khái niệm thì đã có trong file pdf  cùng thư mục này. Hãy dành chút thời gian đọc nó nhé Nam

## Xin nhớ cho!

```
“Any fool can write code that a computer can understand. Good programers write code that humans can understand.” 

Tạm dịch : 

“Bất kỳ kẻ ngốc nào cũng có thể viết mã mà máy tính có thể hiểu được. Các lập trình viên giỏi viết mã mà con người có thể hiểu được ”.

```

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>