# Open/Closed Principle

- nó có nghĩa là : Có thể mở rộng 1 class, nhưng không được sửa đổi bên trong class đó

- wtf cái méo j vậy các cụ có câu "Bất Nhập hổ huyệt , bất đắc hổ tử" , mày lại xạo đúng không , mở rộng ra mà không sửa nó , điêu nó quen đi
- không hề nhé trong lập trình không gì là không thể trừ một vài cái không làm dk
- Theo nguyên lý này, mỗi khi ta muốn thêm chức năng,.. cho chương trình, chúng ta nên viết class mới mở rộng class cũ ( bằng cách kế thừa hoặc sở hữu class cũ) không nên sửa đổi class cũ.
- lại lấy vd đi , bạn có 1 class có sẵn rồi và 30 class kacs thừa kế nó nhưng bạn không thích trả về kiểu string chẳng hạn , bạn thích kiểu bool giống mình thì bạn sửa 1 cái , uỳnh . cụ đi chân lạnh toát , 
## giải pháp
 VD : B thừa kế A , bạn muốn thêm 1 tính năng khác mà class A chưa có thì bạn bạn nên tạo 1 class mới và kế thừa lại A và cho tính năng đó vào (TÍnh năng nó cả trăm class lấy vd nhé) , đó thế là cụ vẫn chưa đi vẫn dk 100 năm dương thọ heheehe