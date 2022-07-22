# Dealing with Generalisation

Trừu tượng có một nhóm kỹ thuật tái cấu trúc riêng, chủ yếu liên quan đến việc di chuyển chức năng dọc theo hệ thống phân cấp kế thừa class, tạo ra các class và interface mới, đồng thời thay thế kế thừa bằng ủy quyền và ngược lại.

1. Pull Up Field 

Hai class con có cùng field. Di chuyển field vào class cha.

2. Pull Up Method 

Chúng ta có các method có kết quả giống hệt nhau trên các class con. Di chuyển chúng đến class cha.

3. Pull Up Constructor Body

Chúng ta có các hàm tạo trên các class con với hầu hết là các phần tử đồng nhất. Tạo một method khởi tạo class cha; gọi điều này từ các method của class con.

4. Push Down Method

Hành vi trên class cha chỉ phù hợp với một số class con của nó. Di chuyển nó đến các class con đó.

5. Push Down Field 

Một field chỉ được sử dụng bởi một số class con. Di chuyển field đến các class con đó.

6. Extract Subclass 

Một class có các tính năng chỉ được sử dụng trong một số trường hợp . Tạo một class con cho tập hợp con các tính năng đó.

7. Extract Superclass 

Chúng ta có hai class con với các tính năng tương tự. Tạo một class cha và di chuyển các đặc điểm chung vào class cha.

8. Extract Interface

Một số client sử dụng cùng một tập hợp con của interface một class hoặc hai class có chung một phần interface của chúng.

9. Collapse Hierarchy

Class cha và class con không khác nhau lắm. Hợp nhất chúng lại với nhau.

10. Form Template Method

Chúng ta có hai method trong các class con thực hiện các bước tương tự theo cùng một thứ tự, tuy nhiên các bước thực hiện khác nhau. Nhận các bước thành các method có cùng signature, để các method ban đầu trở nên giống nhau. Sau đó, Chúng ta có thể kéo chúng lên.

11. Replace Inheritance with Delegation 

Một class con chỉ sử dụng một phần của interface class cha hoặc không muốn kế thừa hoặc không muốn kế thừa dữ liệu. Tạo một field cho class cha, điều chỉnh các method để ủy quyền cho class cha và loại bỏ class con.

12. Replace Delegation with Inheirtance

Chúng ta đang sử dụng ủy quyền và thường viết nhiều ủy quyền đơn giản cho toàn bộ interface. Đặt class ủy nhiệm thành một class con của ủy nhiệm.

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>