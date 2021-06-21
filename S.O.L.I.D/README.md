# S.O.L.I.D

> SOLID là từ viết tắt của năm nguyên tắc thiết kế hướng đối tượng (OOD) đầu tiên của Robert C. Martin (còn được gọi là Uncle Bob).

> Các nguyên tắc này thiết lập các thông lệ cho phép phát triển phần mềm với các cân nhắc để duy trì và mở rộng khi dự án phát triển. Việc áp dụng các phương pháp này cũng có thể góp phần tránh code smells, refactoring code và phát triển phần mềm Agile or Adaptive.

1. SOLID là viết tắt của:

* S : Single responsibility priciple (SRP) 
> Mỗi lớp chỉ nên chịu trách nhiệm về một nhiệm vụ cụ thể nào đó.
* O : Open/Closed principle (OCP) 
> Không được sửa đổi một Class có sẵn, nhưng có thể mở rộng bằng kế thừa.
* L : Liskov substitution principe (LSP) 
> Các đối tượng (instance) kiểu class con có thể thay thế các đối tượng kiểu class cha mà không gây ra lỗi.
* I : Interface segregation principle (ISP) 
> Thay vì dùng 1 interface lớn, ta nên tách thành nhiều interface nhỏ, với nhiều mục đích cụ thể.
* D : Dependency inversion principle (DIP) 
> Các module cấp cao không nên phụ thuộc vào các modules cấp thấp. Cả 2 nên phụ thuộc vào abstraction. Và Interface (abstraction) không nên phụ thuộc vào chi tiết, mà ngược lại (Các class giao tiếp với nhau thông qua interface (abstraction), không phải thông qua implementation.)