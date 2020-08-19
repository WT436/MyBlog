# Dependency Inversion Principle

1. Các module cấp cao không nên phụ thuộc vào các modules cấp thấp.Cả 2 nên phụ thuộc vào abstraction.
2. Interface (abstraction) không nên phụ thuộc vào chi tiết, mà ngược lại.( Các class giao tiếp với nhau thông qua interface,không phải thông qua implementation.)

- đọc xong mà không xỉu chắc tui cx phục
- ok các bạn thường làm như thế nào khi muốn gọi 1 function trong 1 class ohhh chắc sẽ là new class đó đúng không không nói đến mấy ban biết DI nhé , thế là cụ đi chân ak mà thôi
- khi gọi ra các ban chỉ được phép gọi cái thằng interface của nó , không gọi trực tiếp
- tức là ntn , anh A gọi anh B thì chỉ cần biết anh B có thẻ làm đk công việc B1 mà không biết anh B làm ntn
  trên thực tế các dự án thường cđược chia ra nhiều tầng khác nhau các tầng trên tiệm cận vs người dùng thì không quá phụ thuộc vào các class thực thi , mà chỉ phụ thuộc vào interface của class đó , để nếu chúng ta có sửa class hay đổi tên class thì không làm ảnh hưởng đến toàn bộ chương trình
- ngẫm lại đi chứ mk nói thêm một chút nữa chắc mk cx nghẻo luôn 
