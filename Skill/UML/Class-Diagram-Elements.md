# Class Diagram Elements

Class Diagram là một trong những loại Diagram hữu ích nhất trong UML vì chúng vạch ra rõ ràng cấu trúc của một hệ thống cụ thể bằng cách mô hình hóa các Class, properties, action và mối quan hệ giữa các đối tượng của nó.

## Giai đoạn thiết kế

Design: xác định cấu trúc của hệ thống phần mềm sẽ được viết như thế nào và hoạt động như thế nào, mà không thực sự viết bản triển khai hoàn chỉnh.

Sự chuyển đổi từ "What" hệ thống phải làm, sang "How" hệ thống sẽ làm điều đó. Vì vậy hãy đặt những câu hỏi What mà tôi hay tự hỏi chính bản thân mình:

- Chúng ta sẽ cần những lớp nào để triển khai một hệ thống đáp ứng các yêu cầu? 
- Mỗi lớp sẽ có những fields và methods nào? 
- Các lớp sẽ tương tác với nhau ra sao?

## Vậy làm thế nào để thiết kế ra chúng.

I. Xác định tất cả các lớp spec / requirements
- xác định tất cả danh từ chủ chốt của classes, objects, fields
- xác định tất cả các động từ là tiềm năng , chủ lực của một class

![image](https://user-images.githubusercontent.com/63473793/123304679-6d6b2780-d549-11eb-8d40-c7dc4058ff99.png)

_Chú Ý :_
```
• UML class diagram: hình ảnh của
- các lớp trong hệ thống OOP
- các lĩnh vực và phương pháp 
- kết nối giữa các lớp
• tương tác hoặc kế thừa lẫn nhau
• Không được biểu diễn trong class diagram UML:
- chi tiết về cách các class tương tác với nhau
- chi tiết thuật toán, một hành vi cụ thể như thế nào thực hiện
```
2. Các quy định căn bản

* tên lớp ở đầu hộp
  - viết <<interface>> lên trên tên của các giao diện
  - sử dụng chữ nghiêng cho tên lớp trừu tượng
 
 ![image](https://user-images.githubusercontent.com/63473793/123370642-590b4700-d5aa-11eb-8e25-69034ef5c159.png)
 
* thuộc tính (tùy chọn)
  - nên bao gồm tất cả các trường của đối tượng
* hoạt động / phương pháp (tùy chọn)
  - có thể bỏ qua các phương thức tầm thường (get / set)
* nhưng không bỏ qua bất kỳ phương thức nào khỏi Interface!
  - không nên bao gồm các kế thừa
 
 3. với các attributes
 
– visibility: 
```
+ public
# protected
- private
~ package (default)
/ derived
```
- với các static attributes phải gạch chân
- parameter được ghi dưới dạng (name: type)
- Method : methodExample(parameter1: String, parameter2: Int): double 
 
4. Comments
 
 ![image](https://user-images.githubusercontent.com/63473793/123371386-e56a3980-d5ab-11eb-8e84-4247b09992f7.png)

 II. Các mối quan hệ tổng quát (kế thừa)

- các cấu trúc phân cấp được vẽ từ trên xuống.
- mũi tên hướng lên cha mẹ
 • kiểu dòng / mũi tên cho biết cha mẹ có phải là a (n):
- Class : nét liền mảnh, mũi tên đen
- abstract class: đường liền nét, mũi tên trắng
- Interface : đường đứt nét, mũi tên trắng
 
 ![image](https://user-images.githubusercontent.com/63473793/123375931-d1c2d100-d5b3-11eb-9240-f8bf73b1a3d0.png)

 III. Mối quan hệ liên kết (Associational relationships)
 
```
(1) đa dạng hóa
    • *       ⇒  0, 1 hoặc nhiều hơn
    • 1       ⇒  1 chính xác
    • 2..4    ⇒  từ 2 đến 4, bao gồm
    • 3 .. *  ⇒  3 hoặc nhiều hơn (còn được viết là “3 ..”)
(2) mối quan hệ của các đối tượng
(3) điều hướng
```
 
 ![image](https://user-images.githubusercontent.com/63473793/123376316-7cd38a80-d5b4-11eb-9954-061a96661756.png)

IV. Đa dạng hóa
 
 1. one to one
   * để hiểu hơn chúng ta chỉ cần nhìn vào bức ảnh này 
 
   ![image](https://user-images.githubusercontent.com/63473793/123377955-8827b580-d5b6-11eb-9144-989bab77b15d.png)

   > mỗi sinh viên phải mang đúng một thẻ ID
 2. one to many
  * để hiểu hơn chúng ta chỉ cần nhìn vào bức ảnh này 
 
  ![image](https://user-images.githubusercontent.com/63473793/123378248-b2797300-d5b6-11eb-9330-1101d40d56e9.png)
 
  > một danh sách hình chữ nhật có thể chứa nhiều hình chữ nhật

V. Các loại liên kết
 
 1. aggregation 
 
   > thần chú : "là một phần của"
 
   ![image](https://user-images.githubusercontent.com/63473793/123378590-2c116100-d5b7-11eb-884d-7a324eb42dfb.png)
 
   ```  
    được biểu tượng bằng một viên kim cương trắng trong
   ```
 
 2. composition
 
   > thần chú : "Hoàn toàn được làm bằng"
 
   ![image](https://user-images.githubusercontent.com/63473793/123378617-33386f00-d5b7-11eb-92bb-eb033fb650a9.png)
 
   ```
    - phiên bản tổng hợp mạnh mẽ hơn
    - các bộ phận sống và chết với toàn bộ
    - được biểu tượng bằng một viên kim cương đen
   ```

 3. dependency
 
   > thần chú : "Sử dụng tạm thời"
 
   ![image](https://user-images.githubusercontent.com/63473793/123378655-3d5a6d80-d5b7-11eb-81f4-70a331e03077.png)

   ```
   - được ký hiệu bằng đường chấm
   - thường là một triển khai chi tiết, không phải là một phần nội tại của trạng thái của đối tượng đó
   ```
 VI. Ví Dụ
 
 ![image](https://user-images.githubusercontent.com/63473793/123387891-75b37900-d5c2-11eb-9182-a2063dbaecd1.png)

  <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>