### Thread và Task

| Máy tính và hệ điều hành |
|---|

+ Trước khi tìm hiểu chúng, chúng ta cần phân biệt số lõi số luồng và lập lịch sử lý : 
  - Nhân và luồng CPU là gì? -- tự đi mà tìm hiểu.
  - Lập lịch sử lý là gì? (Tiến trình trong hệ điều hành) Tiếp tục tự đi mà tìm hiểu.
+ Điều đầu tiên tôi muốn thay đổi là thay đổi cách gọi :
  - Task : Nhiệm vụ sử lý trên luồng
  - ![image001](https://user-images.githubusercontent.com/63473793/169646865-aec42d19-e962-4fb5-87a0-40692abad110.gif)
  - Thread : Luồng sử lý
  - ![image002](https://user-images.githubusercontent.com/63473793/169646870-c9920872-9bc6-49e2-9afe-9c8dd8e3d35a.gif) 

| Thread |
|---|
- Theo tôi trong thread nói chung không có khái niệm lập trình bất đồng bộ mà chỉ có chia khối lượng việc ra cho nhiều luồng sử lý. Tức là thread là một chuỗi các lệnh được lập trình có thể quản lý độc lập bởi bộ lập lịch. Một thread là một thành phần của một tiến trình, một tiến trình thì có thể có nhiều thread, có thể thực thi đồng thời và chia sẻ tài nguyên như CPU, RAM, … trong khi các tiến trình thì không chia sẻ các tài nguyên này.
- Nói cách khác Hệ điều hành sẽ điều phối lõi CPU nào vào việc và số thread không vượt qua số core or thread của cpu (cái này không nhớ rõ lắm) 

| Task |
|---|

+ Synchronous (đồng bộ) là một tiến trình xử lý các công việc theo thứ tự đã được định sẵn. Công việc phía sau phải đợi công việc phía trước hoàn thành thì mới bắt đầu thực hiện. Trong lập trình, một chương trình đồng bộ là một chương trình được thực hiện theo từng câu lệnh từ trên xuống dưới, từ trái qua phải, câu lệnh sau chỉ được thực hiện khi câu lệnh phía trước hoàn thành.

+ Asynchronous (bất đồng bộ), là tiến trình mà việc xử lý các công việc được thực hiện đồng thời cùng lúc. Công việc sau không phải chờ đợi công việc phía trước hoàn thành thì mới bắt đầu thực hiện mà thay vào đó, cả hai công việc sẽ cùng được thực hiện cùng lúc.

| Phân biệt Thread và Task |
|---|
+ Ở đây tôi sẽ dựa vào ví dụ của microsoft : Bữa sáng

+ Bài toán : Một công ty có 100 nhân viên. Công ty phải chuẩn bị bữa sáng cho nhân viên của mình. Tuần tự của mỗn nhân viên như sau : 
  - Pha cà phê
  - Đặt chảo
  - Rán trứng
  - Chiên thịt
  - Nướng bánh mỳ
  - Kẹp bánh
  - Pha nước hoa quả
  
![image](https://user-images.githubusercontent.com/63473793/169647732-426d8b54-451e-4b36-9fdd-f8150e1660a2.png)

Mỗn chuỗi công việc mất ít nhất 15p. Hãy làm cho tổng thời gian làm bữa sáng cho 100 nhân viên nhanh nhất. (Công ty có 12 nhân viên làm bữa sáng)

=> Tổng thời gian nếu chỉ có 1 nhân viên phục vụ bữa sáng : 100* 15 = 1,500 phút

=> Nếu là thread chỉ đơn giản là 12 nhân viên làm bữa sáng đó cùng lúc phục vụ 12 nhân viên đi làm => Tổng thời gian  = 100 * 15 / 12 = 125 phút

=> Còn Task sẽ là 1 nhân viên phục vụ tiết kiệm bằng cách bỏ qua thời gian chờ chờ chảo nóng và bánh mỳ nóng. Tức lúc pha cà phê thì anh ta có thể đã đặt chảo và cho bánh mỳ vô rồi. Lúc cà phê đến thì chảo đã nóng. Lúc rán chứng và chiên thịt xong thì bánh mỳ cũng đã sẵn sàng. 

  - Thay vì pha cà phê => đặt chảo => chờ chảo nóng => chiên thịt => chiên trứng => đặt bánh mỳ => chờ bánh mỳ nóng => kẹp bánh => pha nước hoa quả.

=> Chúng ta sẽ tiết kiệm dk 5 phút "CHỜ" => 10 * 100 = 1000

![image](https://user-images.githubusercontent.com/63473793/169648135-de650fb6-e077-46d8-b75c-e109c71d5098.png)

=> Khi đã có kế hoạch thì mọi chuyện sẽ nhanh hơn rất nhiều. Khi đã có nhiều người chia nhỏ số luongj công việc ra thì sẽ rất nhanh.

=> Kết Hợp cả hai => 10 * 100 / 12 = 83,333

+ Điểm mạnh
+ Điểm yếu

| Kết hợp Thread và Task |
|---|

| Vấn đề của Thread và Task |
|---|

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>