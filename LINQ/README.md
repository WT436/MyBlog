# LinQ c#

LINQ (Language Integrated Query) là một tập hợp các tính năng được giới thiệu trong .NET Framework 3.5 nhằm thu hẹp khoảng cách giữa Object và Data.

Thông thường các truy vấn đối với Data được thể hiện dưới dạng các chuỗi đơn giản mà không cần kiểm tra kiểu tại thời điểm biên dịch hoặc hỗ trợ IntelliSense. Hơn nữa, bạn phải học một ngôn ngữ truy vấn khác nhau cho từng loại nguồn dữ liệu: cơ sở dữ liệu SQL, tài liệu XML, các dịch vụ Web khác nhau, v.v. LINQ làm cho một truy vấn trở thành một cấu trúc ngôn ngữ hạng nhất trong C# và VB. Bạn viết các truy vấn chống lại các tập hợp các đối tượng được đánh máy mạnh bằng cách sử dụng các từ khóa ngôn ngữ và các toán tử quen thuộc.

Các truy vấn LINQ trong c# đều làm việc với object và thao tác trên Data.

Với XML chúng ta có LINQ to XML , Với Database chúng ta có LINQ to SQL, Với ADO.Net DataSet chúng ta có LINQ To DataSet , Với Object Collection chúng ta có LINQ To Object, Với Entity Framework chúng ta có LINQ To Entities..... 
## Khai Báo

Trong c# Linq đã được tích hợp thẳng vào lõi hệ thống .Net trong file System. Vì vậy để sử dụng được linq chúng ta chỉ cần khai báo namespace:

``` c#
 using System;
 using System.Linq;
```

## Tại sao chúng ta nên dùng LINQ.

- Tận dụng tối đa điểm mạnh của delegate.
- Không cần đến các vòng lặp lằng ngoằng.
- Mã sẽ nhỏ gọn và dễ đọc hơn vì có biểu thức lambda.
- Triển khai các loại List khác nhau nhưng kết quả chỉ cần một câu lệnh.
- Truy vấn được các nguồn dữ liệu khác nhau.
- ......

## Vậy ưu điểm của nó là gì mà lại được ưa chuộng như vậy?

- Hỗ trợ IntelliSense : LINQ cung cấp IntelliSense cho list kiểu generic.
- An toàn khi biên dịch các câu truy vấn : Nó kiểm tra các kiểu của Object khi biên dịch.
- Code Dễ đọc hơn: 
- Viết ít hơn :
- TRuy vấn chuẩn hóa nhiều nguồn dữ liệu về một dạng cú pháp:
- Định hình dữ liệu:
- Ngôn ngữ thân thuộc:

## Cách viết

Có 2 cách viết LINQ đó là : LINQ và Lambda

1. Linq thì từ đời đầu : 
2. Lambda thì có từ c# 3.0 và .NET 3.5

## Cú pháp truy vấn và cú pháp phương thức ( Query Syntax and Method Syntax)

Cú pháp truy vấn và cú pháp phương thức giống hệt nhau về mặt ngữ nghĩa, nhưng nhiều người thấy rằng cú pháp truy vấn đơn giản hơn và dễ đọc hơn. Giả sử chúng ta cần truy xuất tất cả các mục chẵn được sắp xếp theo thứ tự tăng dần từ một tập hợp các số.

## Toán tử phân vùng (Partitioning Operators)

1. Take
2. Skip
3. TakeWhile 
4. SkipWhile

## Các chế độ thực thi (Execution Modes)

1. immediate
2. deferred streaming
3. deferred non-streaming

## Toán tử truy vấn (Standard Query Operators)

Các truy vấn Linq được viết bằng cách sử dụng Toán tử truy vấn chuẩn (là một tập hợp các phương thức mở rộng hoạt động chủ yếu trên các đối tượng thuộc loại IEnumerable <T> và IQueryable <T>) hoặc sử dụng Biểu thức truy vấn (tại thời điểm biên dịch, được chuyển đổi thành Toán tử truy vấn chuẩn các cuộc gọi phương thức).

Toán tử truy vấn cung cấp các khả năng truy vấn bao gồm : filtering, projection, aggregation, sorting and
more.

Phương thức kết nối hiện có:

Concat,Where ,OfType,Join,GroupJoin,Zip,SelectMany,OrderBy,OrderByDescending,ThenBy,ThenByDescending,Reverse,AsEnumerable,AsQueryable,Cast,ToArray,ToList,ToDictionary,Aggregate,Average,Count,LongCount,Max,Min,Min-/MaxOrDefault,Sum, All,Any,Contains,GroupBy,ToLookup,Skip,SkipWhile,Take,TakeWhile,DefaultIfEmpty,Empty,Range,Repeat,Distinct,Except,Intersect,Union,SequenceEqual,,ElementAt,ElementAtOrDefault,First,FirstOrDefault,Last,LastOrDefault,Single,SingleOrDefault

Cách viết và cách dùng như thế nào ra sao thì sẽ có chi tiết trong folder này. Hôm nay đến đây thôi. Tôi phải nói là tôi rảnh v~ cả đạn ra. nhưng tôi sẽ cố lọc ra đầy đủ.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>