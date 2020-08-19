# Sự KHác Biệt Giữa 2 cái này

## abstract function

```
 - nó là một thứ gì đó giống như tiêu đề quấn sách vậy , khi khai báo nó bạn phải ghi đè lên nó , nói sao cho hiểu bây h nhỉ , tóm cái váy lại là nó chỉ có <Vùng truy cập><Kiểu Dữ liệu><Tên hàm >(paramester truyền vào) và ; kết thúc
 - và thằng này nó lười thối thân ra ý , nó chỉ có đưa ra mục cần làm và bắt mấy thằng thừa kế mình phải làm theo (chán lắm )
 - Vùng truy cập chỉ có thể là pub và pro nhé
 - vd public bool Ban-co-yeu-hai-nam-khong(bool traloi);
 - chẳng biết phải chém sao nữa

```

## interface

```
 - interface là interface hay nói cách khác interface là interface ?????? có gì sai sai nhỉ , đúng không interface là interface mà , ờ ha interface là interface ok .
 - interface trong code ý , nó chính là cái khẳng định rằng mi sẽ phải làm những thứ này , hay tôi gọi interface là một bản hợp đồng bắt buộc với những điều khoản bắt buộc mà người tuân thủ phải làm theo , nhưng nó chỉ có các tiêu đề của hợp đồng mà thôi , và nó chỉ có các tiêu đề điều khoản mà thôi
 - một interface chỉ có các hàm abstract và luôn public (abstract function)
```

## abstract class

```
 - câu đầu tiên : abstract class nó là một class nó có tất cả những gì mà class có
 hay nói cách khác nó là sự kết hợp hoàn hảo  của tất cả những gì class có
 -  riêng vs class là nó có abstract function
 - 1 abstract class , nên có 1 abstract function (Nếu không có khai báo abstract class chi cho nó đau đầu nhể)
 -phạm vi , pro và pub nhé
```

## KHác biệt

```
- khả năng kế thừa , interface thì thỏa con gà mái nhé  thằng này mất dậy thích đánh nhau nhưng lại thích " càng đông càng vui ", còn abstract class thì thích đánh nhau 1v1 (Ọe yếu sinh lý thì nó ra đê ) đùa thôi đa kế thừa nó là một cái gì mà mình hay nói là tự tay bóp ..... ak thôi
-   has-a và is-a
    - một cái là  "có thể là" và một cái là  "là" giống như nhìn 1 chàng trai thì có thể là 0 hoặc 1 . nhìn 1 con người là 1 con người ??? lại nói cái mẹ gì không biết ??????
- khi sử dụng abstract class thì nó là 1 class nên chúng ta có thể dùng nó như 1 class bình thường
- vấn đề runtime nữa , ak mà thôi cái này sẽ nói trong pattern nhóe
vd: 1 abstract class có 2 abstract function và 2 function bình thường thì chúng ta chỉ phải thừa kế 2 abstract function mà thôi 2 cái kia base nó vào cx đk mà không cũng đk còn interface thì no never (thằng interface này nó gia trưởng lắm động vào nó là phải nghe lời nó)
- interface nó không thể chứa data đk ,quay lại với ông bảo thủ này , bảo ông ấy cầm cho 1 biến kẹo để lưu lại data chẳng hạn .nhưng no no nhất quyết hổng chịu cơ
- còn cái nữa về ông  đần này là nó cx  hổng có chịu constructor và deconstructor (hàm tạo và hàm hủy) vì đơn giản nó có new dk đâu :))
- lại thêm 1 cái khóc giở ms thằng interface này là nó (interface) chỉ có chịu kế thừa của interface khác mà thôi , nhưng lại cho phép ở các  interface khác ở chung nhà vs 1 cô gái class của mình (1 class có thể kế thừa  nhiều interface) ôi đàn bà là những niềm đau
- abstract class là class nên nó là 1 class ???? nói cái j vậy mài . ờ thì bản chất nó là 1 class nên nó là 1 class . ??? thôi nghỉ đi
```

## khi nào dùng thằng nào

```
khi bạn muốn tất cả những class phải làm theo mình thì dùng interface  , khi bạn chỉ muốn các class thừa kế dùng những gì mà bạn cho là tất cả các classs phải có và muốn có hoặc không có thì dùng abstract class
.......................................................
```
