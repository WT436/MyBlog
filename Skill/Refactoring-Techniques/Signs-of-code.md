# Signs of code that might need refactoring

Cuối cùng hãy nhận biết tất cả chúng và sử lý tận gốc những vấn đề phát sinh.

1. Duplicated ( Code Mã trùng lặp )

Được chứng minh nếu việc cut-and-paste được thực hiện nhiều lần.

> Extract Method, Extract Class, Pull UP Method, Form Template Method

2. Long Method (Hàm quá dài)

Nếu bạn đang cuộn màn hình trên màn hình khi thực hiện cùng một phương thức, có thể bạn có một phương thức quá dài

> Extract Method, Replace Temp with Query 

3. Large Class (Class quá khổng lồ)

Có thể hiển thị dưới dạng quá nhiều biến phiên bản. Bạn có thể cần phải phân rã tốt hơn thành các lớp phục vụ hoặc cách khác.

> Extract Class, Extract Subclass, Extract Interface, Replace Data Value with Object

4. Long Parameter List (số lượng tham số quá chi là khủng khiếp)

Danh sách tham số quá lớn hoặc nếu bạn có các tham số tùy chọn. Được chứng minh nếu một số tham số không được sử dụng.

> Replace Parameter with Method, Introduce Parameter Object, Preserve Whole Object 

5. Divergent Change

Khi một lớp đơn lẻ được thay đổi quá thường xuyên khi các thay đổi được yêu cầu. Chức năng có thể cần được trích xuất thành các lớp hoặc phương thức riêng biệt.

> Extract Class 

6. Shotgun Surgery 

Khi xảy ra sự thay đổi thay đổi môi trường hệ thống, bạn phải chỉnh sửa nhiều lớp.

> Move Method, Move Field, Inline class

7. Feature Envy 

Khi một lớp khác phụ thuộc vào một lớp khác để cung cấp một chức năng nhất định, một lớp khác có thể thực sự cần thực hiện chức năng đó.

> Move Method, Move Field, Extract Method 

8. Data Clumps

Đây là các bit dữ liệu phân tán thuộc về nhau nhưng vẫn tồn tại trong các lớp / phương thức khác nhau.

> Extract Class, Introduce Parameter Object

9. Primitive Obsesssion

Thời gian tương đối để di chuyển đến các đối tượng và giữ các trường dưới dạng các kiểu nguyên thủy riêng biệt

> 

10. Switch Statements

Quá nhiều câu lệnh switch hiển thị các câu lệnh thủ tục.

> Replace Conditional with Polymorphism, Replace Type Code with Subclasses, Replace Type Code with State/Strategy, Replace Parameter with Explicit Methods, Introduce Null Objects

11. Parallel Inheritance Hierarchies

Trường hợp đặc biệt của phẫu thuật súng ngắn, trong đó mỗi khi bạn phân loại một lớp này, bạn sẽ phải phân lớp khác.

> Move Method, Move Field 

12. Lazy Class 

Một lớp không kéo trọng lượng của nó.

> Inline Class, Collapse Hierarchy

13. Speculative Generality 

Việc sử dụng các lớp trừu tượng hoặc siêu phương thức phải được ghi đè để hữu ích. Các dấu hiệu cần tìm nếu những thứ duy nhất sử dụng nó là các trường hợp thử nghiệm.

> Collapse Hierarchy, Inline Class, Remove Parameter, Rename Method 

14. Temporary Field 

Một biến thể hiện chỉ được đặt trong một số trường hợp nhất định.

> Extract Class, Introduce Null Object 

15. Message Chains 

Được thể hiện khi một khách hàng yêu cầu một đối tượng cho đối tượng antoher, mà sau đó khách hàng yêu cầu một đối tượng khác, v.v. Có một khớp nối mạnh mẽ ở đây.

> Hide Delegate 

16. Middle Man

Nếu một phương thức chỉ đơn giản là chuyển các tham số cho một phương thức khác mà không cung cấp chức năng thực, có thể là một ứng cử viên tốt để tái cấu trúc.

> Remove Middle Man, Inline Method, Replace Delegation with Inheritance

17. Inappropriate Intimacy 

Khi các lớp xử lý các biến riêng tư hoặc được bảo vệ trong một lớp khác quá thường xuyên. Phổ biến trên hệ thống phân cấp kế thừa.

> Move Method, Move Field, Chagne Bidirectional Association to Unidirectional, Replace Inheritance with Delegation, Hide Delegate

18. Alternative Classes with Different Interfaces 

Khi một lớp khác làm cùng một công việc được tạo chỉ cho một chữ ký khác. Điều này nên được thay thế bằng quá tải và hợp nhất thành một lớp duy nhất.

> Rename Method, Move Method 

19. Incomplete Library Class

Khi chức năng thư viện không cung cấp bộ hoàn chỉnh cần thiết (thường là khi bạn được cung cấp một thư viện để làm việc với bên ngoài tổ chức hoặc dự án của bạn).

> Introduce Foreign Method, Introduce Local Extension

20. Data Class

Chủ sở hữu dữ liệu câm có thể cung cấp chức năng tốt hơn nếu được giao nhiều việc hơn.

> Move Method, Encapsulate Field, Encapsulate Collection

21. Refused Bequest 

Khi một lớp con không muốn các phương thức vốn có trong lớp cha.

> Repleace Inheritance with delegation 

22. Comments

Mặc dù nhận xét là rất tốt, nhưng việc tái cấu trúc có thể khiến hầu hết các nhận xét trở nên thừa. Nếu một phương thức được nhận xét nhiều, nó có thể cần cấu trúc lại

> Extract Method, Introduce Assertion 