#  Method execution modes

 thực thi việc trì hoãn lấy dữ lieeuk so với phải lấy ngay dữ liệu. Giúp tăng tốc độ truy vấn. Hiểu nôm la là Chúng ta có 1 tỷ bản ghi, và để lấy đống đó ra thì mất rất rất nhiều thời gian. vì vậy LINQ sẽ thực thi query object và nó không giữ kết quả của câu truy vấn. thay vào đó, nó có tất cả thông tin cần thiết để tạo ra những kết quả đó

##  Xem ví dụ sau

```c#
var list = new List<int>() {1, 2, 3, 4, 5};
var query = list.Select(x => {
 Console.Write($"{x} ");
 return x;
});

```

Truy vấn chứa một cuộc gọi đến Console.Write, nhưng không có gì được xuất ra bảng điều khiển. Điều này là do truy vấn chưa được thực hiện, và do đó, hàm được chuyển đến Chọn chưa bao giờ được đánh giá. Điều này được gọi là thực thi hoãn lại - việc thực thi truy vấn bị trì hoãn cho đến một thời điểm nào đó sau đó.

Các phương thức LINQ khác buộc thực hiện truy vấn ngay lập tức; các phương thức này thực thi truy vấn và tạo ra các giá trị của nó:
```c#
var newList = query.ToList();
```
> Kết qua được : 1 2 3 4 5

Nói chung, các phương thức LINQ trả về một giá trị duy nhất (chẳng hạn như Max hoặc Count) hoặc trả về một đối tượng thực sự giữ các giá trị (chẳng hạn như ToList hoặc ToDictionary) sẽ thực thi ngay lập tức.

Các phương thức trả về IEnumerable <T> hoặc IQueryable <T> đang trả về đối tượng truy vấn và cho phép trì hoãn việc thực thi cho đến thời điểm sau đó.

## So sánh Streaming mode (lazy evaluation) vs non-streaming mode (eager evaluation)

Trong số các phương thức LINQ sử dụng thực thi hoãn lại, một số phương pháp yêu cầu một giá trị duy nhất được đánh giá tại một thời điểm. Ví dụ ngay:

```c#
var lst = new List<int>() {3, 5, 1, 2};
var streamingQuery = lst.Select(x => {
 Console.WriteLine(x);
 return x;
});
foreach (var i in streamingQuery) {
 Console.WriteLine($"foreach iteration value: {i}");
}
```
Kết Quả là :

```
3
foreach iteration value: 3
5
foreach iteration value: 5
1
foreach iteration value: 1
2
foreach iteration value: 2
```

bởi vì hàm được truyền cho Select được đánh giá tại mỗi lần lặp lại của foreach. Đây được gọi là  streaming mode or lazy evaluation.


Các phương thức LINQ khác - toán tử sắp xếp và nhóm - yêu cầu tất cả các giá trị phải được đánh giá, trước khi chúng có thể trả về bất kỳ giá trị nào:

```c#
var nonStreamingQuery = lst.OrderBy(x => {
 Console.WriteLine(x);
 return x;
});
foreach (var i in nonStreamingQuery) {
 Console.WriteLine($"foreach iteration value: {i}");
}
```

Kết quả là :

```
3
5
1
2
foreach iteration value: 1
foreach iteration value: 2
foreach iteration value: 3
foreach iteration value: 5
```

Trong trường hợp này, bởi vì các giá trị phải được tạo cho foreach theo thứ tự tăng dần, tất cả các phần tử trước tiên phải được đánh giá, để xác định cái nào là nhỏ nhất và cái nào là nhỏ nhất tiếp theo, v.v. Đây được gọi là  non-streaming mode or eager evaluation.

## LỢi ích của deferred execution - building queries

- Deferred execution cho phép kết hợp các hoạt động khác nhau để tạo truy vấn cuối cùng, trước khi đánh giá các giá trị

- Với Deferred execution, nếu dữ liệu được truy vấn bị thay đổi, đối tượng truy vấn sẽ sử dụng dữ liệu tại thời điểm thực thi, không phải tại thời điểm xác định.