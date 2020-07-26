Hủy đối tượng

Ngôn ngữ C# cung cấp cơ chế thu dọn (garbage collection) và do vậy không cần phải
khai báo tường minh các phương thức hủy. Tuy nhiên, khi làm việc với các đoạn mã
không được quản lý thì cần phải khai báo tường minh các phương thức hủy để giải
phóng các tài nguyên.

C# cung cấp ngần định một phương thức để thực hiện điều khiển công việc này, phương
thức đó là Finalize() hay còn gọi là bộ kết thúc. Phương thức Finalize này sẽ được gọi
bởi cơ chế thu dọn khi đối tượng bị hủy.

Phương thức kết thúc chỉ giải phóng các tài nguyên mà đối tượng nắm giữ, và không
tham chiếu đến các đối tượng khác. Nếu với những đoạn mã bình thường tức là chứa
các tham chiếu kiểm soát được thì không cần thiết phải tạo và thực thi phương thức
Finalize().
 Chúng ta chỉ làm điều này khi xử lý các tài nguyên không kiểm soát được.

Chúng ta không bao giờ gọi một phương thức Finalize() của một đối tượng một cách
trực tiếp, ngoại trừ gọi phương thức này của lớp cơ sở khi ở bên trong phương thức
Finalize() của chúng ta. Trình thu dọn sẽ thực hiện việc gọi Finalize() cho chúng ta.

Bộ hủy của C#

Cú pháp phương thức hủy trong ngôn ngữ C# cũng giống như trong ngôn ngữ C++.
Nhưng về hành động cụ thể chúng có nhiều điểm khác nhau. Ta khao báo một phương
thức hủy trong C# như sau:

~Class1() {}

Tuy nhiên, trong ngôn ngữ C# thì cú pháp khai báo trên là một shortcut liên kết đến một
phương thức kết thúc Finalize được kết với lớp cơ sở, do vậy khi viết
~Class1() { // Thực hiện một số công việc } Cũng tương tự
như viết : Class1.Finalize() { // Thực hiện một số công
việc base.Finalize(); }

Do sự tương tự như trên nên khả năng dẫn đến sự lộn xộn nhầm lẫn là không tránh
khỏi, nên chúng ta phải tránh viết các phương thức hủy và viết các phương thức Finalize
tường minh nếu có thể được.
