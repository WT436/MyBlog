# Query Syntax and Method Syntax

Có 2 cách viết LINQ đó là Query Syntax and Method Syntax cho ollection IEnumerable hoặc IQueryable. Chúng giống nhau về mặt ngữ nghĩa, cho nên rất hay nhầm giữa các loại này với nhau. theo ý kiến cá nhân đánh giá thì Method Syntax dễ dùng hơn. nhưng Query Syntax lại thân thiện hơn.

Vd như các câu lệnh join ....

## Query Syntax

Loại này khá thân thiện và giống tương đối với các câu lệnh dùng để Query Database , cùng xem một ví dụ đơn giản sau :

``` c# 
int[] numbers = { 0, 1, 2, 3, 4, 5, 6 };
// Query syntax:
IEnumerable<int> numQuery1 =
 from num in numbers
 where num % 2 == 0
 orderby num
 select num;
```

Về tổng quan Query Syntax sẽ có cấu trúc như sau :

```
from <range variable> in <IEnumerable<T> or IQueryable<T>>

<toán tử truy vấn> <lambda expression>

<select or groupBy operator> <thành phần cần lấy>
```

Nó sẽ bắt đầu bằng from và luôn kết thúc bằng select or groupBy. khác một chút với query sql

Ohh dễ quá. vậy cần nhớ những gì :

- NÓ khá giống Query SQL.
- Nó sẽ bắt đầu bằng from và luôn kết thúc bằng select or groupBy.
- Nó dùng toán tử filtering, joining, grouping, sorting để tạo ra kết quả mong muốn.
- var có thể dùng cho Query Syntax

## Method Syntax

Chúng ta xem lại ví dụ trên và dùng Method Syntax :
```c#
int[] numbers = { 0, 1, 2, 3, 4, 5, 6 };
// Method syntax:
IEnumerable<int> numQuery2 = numbers.Where(num => num % 2 == 0).OrderBy(n => n);
```

Trông nó khá thân thiện và quen thuộc đúng không?

Method Syntax hay còn được gọi là fluent syntax nó tận dụng extension Enumerable hoặc Queryable. Tương tự như cách bạn gọi phương thức mở rộng của bất kỳ lớp nào.

Trình biên dịch chuyển đổi query syntax thành method syntax tại thời điểm biên dịch.

Để hiểu rõ hơn thằng này chúng ta cần hiểu rx các phương thức có trong Enumerable hoặc Queryable có trong folder c# hoặc tại folder này.

vậy cần nhớ những gì :

- Cái tên nói lên tất cả, Method Syntax giống như gọi extension method.
- var có thể dùng cho Query Syntax
.......

Tổng quan lại : 
- Hãy nhớ rằng một số queries phải được thể hiện dưới dạng method calls. Ví dụ: bạn phải sử dụng một method calls để thể hiện một truy vấn lấy số lượng phần tử phù hợp với một điều kiện được chỉ định. Bạn cũng phải sử dụng method calls cho truy vấn truy xuất phần tử có giá trị lớn nhất trong chuỗi nguồn. Vì vậy, đó có thể là một lợi thế của việc sử dụng method syntax để làm cho mã nhất quán hơn. Tuy nhiên, tất nhiên bạn luôn có thể áp dụng phương pháp này sau khi gọi query syntax

- còn một thứ nữa , đó là "parse the method's IL" nó không dùng cho kẻ yếu tim, nên thôi thứ này sẽ có trong Blog Private.

## nhiều thứ không được phép hiển thị tại đây.

- Tuy giống với Query SQL nhưng Query Syntax lại có nhiều thứ chống lại Query SQL và chúng ta cần tìm hiểu về các cách hỗ trợ chúng như toán tử " LIKE N'A%' " thì sẽ có .StartsWith("A").

Hôm nay đến đây thôi!

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>