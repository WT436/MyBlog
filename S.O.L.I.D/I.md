# Interface Segregation Principle

- Thay vì dùng 1 interface lớn, ta nên tách thành nhiều interface nhỏ, với các mục đích khác nhau

- nghe là hiểu rồi đúng không nào ,  như chúng ta đã biết thì  khi thừa kế 1 interface thì chúng ta phải thừa kế tất cả các function của nó , nó nhỏ thì không sao chứ lớn lên là có chuyện đóa
- vd 1 interface thì có 20 -100 cái function chẳng hạn  ôi trời ơi có những cái cần có những cái khác thì lại không , cụ lại đi chân không chạm đất
- giải pháp chia nhỏ nó ra , vì đơn giản  cần cái nào thì dùng cái ấy
- vậy chia như thế nào , thì đơn giản là  những cái nào liên quan đến vs nhau thì cho vào chung một bộ vậy thui 
- vd như có những con vật  nó có thể đi và bơi như lại không biết bay , h mà cho cả bơi bay và đi 1 interface thì nó phí lắm , nên chia ra 3 interface 