# Design Patterns

## Định nghĩa

Trong kỹ thuật phần mềm, một Design Patterns là một giải pháp có thể lặp lại chung cho một vấn đề thường xảy ra trong thiết kế phần mềm. Một Design Patterns không phải là một Design hoàn chỉnh có thể được chuyển đổi trực tiếp thành Code. Nó là một mô tả hoặc khuôn mẫu về cách giải quyết một vấn đề có thể được sử dụng trong nhiều trường hợp khác nhau.

## Sử dụng liều thuốc an thần này như thế nào? 

Các Design Patterns có thể đẩy nhanh quá trình phát triển bằng cách cung cấp các mô hình phát triển đã được kiểm nghiệm, chứng minh. Thiết kế phần mềm hiệu quả đòi hỏi phải xem xét các vấn đề có thể không được nhìn thấy cho đến khi triển khai sau này. Việc tái sử dụng các Design Patterns giúp ngăn chặn các vấn đề tế nhị có thể gây ra các vấn đề lớn và cải thiện khả năng đọc code cho các lập trình viên và kiến ​​trúc sư quen thuộc với patterns.

Thông thường, mọi người chỉ hiểu cách áp dụng một số kỹ thuật thiết kế phần mềm cho một số vấn đề nhất định. Những kỹ thuật này rất khó áp dụng cho một loạt các vấn đề. Các Design Patterns cung cấp các giải pháp chung, được ghi lại ở định dạng không yêu cầu chi tiết cụ thể gắn với một vấn đề cụ thể.

Ngoài ra, các mẫu cho phép các nhà phát triển giao tiếp bằng cách sử dụng các tên nổi tiếng, được hiểu rõ cho các tương tác phần mềm. Các Design Patterns thông thường có thể được cải thiện theo thời gian, làm cho chúng trở nên mạnh mẽ hơn so với Design Patterns kế đặc biệt.

Nhưng không vì thế mà bạ đâu dùng lấy. dùng nấy dùng nể. dùng vô tội và nó còn đem họa vào source.
Trẻ sơ sinh như tôi cách đây 1 năm thì học thuộc cấu trúc. triển khai dự án cá nhân một cách bất chấp. nhưng rồi nhận ra một điều nếu như dùng mà không chính xác không bao phủ thì có thể gây 'Tẩu hỏa nhập ma' cho cả bộ source. đến một thời điểm nào đó. cần phải thông thạo điểm mạnh điểm yếu của từng D-P thì mới gọi là thông thạo 7.Nhưng thà thử mà thất bại trăm lần còn hơn không dám thử.

## Phân chia thiên hạ

Nói về D-P thì có ty tỷ các loại nhưng ở đây các bậc tiền bối đã chia nó ra làm 3 môn phái và tổng cộng có 23 sư môn cơ bản (có chỗ đề 24 - 25 có chỗ đề 32) đó chính là :

1. Creational D-P

> Các D-P này đều hướng đến sự thể hiện đẳng cấp. Patterns này có thể được chia thành các mẫu tạo class và các Patterns tạo Object. Trong khi các Patterns tạo Class sử dụng hiệu quả kế thừa trong quá trình khởi tạo, các Patterns tạo Object sử dụng ủy quyền một cách hiệu quả để hoàn thành công việc.

    * Abstract Factory
    * Builder
    * Factory Method
    * Object Pool
    * Prototype
    * Singleton

2. Structural D-P

> Các D-P này đều là về thành phần Class và Object. Các Patterns tạo class cấu trúc sử dụng kế thừa để xây dựng Interfaces . Các Patterns Object có cấu trúc xác định các cách xây dựng Object để có được chức năng mới.

    * Adapter
    * Bridge
    * Composite
    * Decorator
    * Facade
    * Flyweight
    * Private Class Data
    * Proxy

3. Behavioral D-P

> Các D-P này đều là về giao tiếp các Object của Class. Các Patterns Behavioral là những mẫu quan tâm cụ thể nhất đến giao tiếp giữa các Object.

    * Chain of responsibility
    * Command
    * Interpreter
    * Iterator
    * Mediator
    * Memento
    * Null Object
    * Observer
    * State
    * Strategy
    * Template method
    * Visitor

Sẽ còn rất rất dài nữa.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>