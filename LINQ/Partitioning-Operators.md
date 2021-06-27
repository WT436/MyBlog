# Partitioning Operators

Partitioning LINQ đề cập đến hoạt động chia chuỗi đầu vào thành hai phần, mà không sắp xếp lại các phần tử, sau đó trả về một trong các phần.

1. Take method

Method Take Đưa các phần tử đến một vị trí xác định bắt đầu từ phần tử đầu tiên trong một chuỗi.

> Public static IEnumerable<TSource> Take<TSource>(this IEnumerable<TSource> source,int count);

```c#
int[] numbers = { 1, 5, 8, 4, 9, 3, 6, 7, 2, 0 };
var TakeFirstFiveElement = numbers.Take(5);
/// Kết quả là 1,5,8,4 và 9 để có được 5 phần tử
```

2. Skip Method

Bỏ qua các phần tử lên đến một vị trí xác định bắt đầu từ phần tử đầu tiên trong một chuỗi.

> Public static IEnumerable Skip(this IEnumerable source,int count);

```c#
int[] numbers = { 1, 5, 8, 4, 9, 3, 6, 7, 2, 0 };
var SkipFirstFiveElement = numbers.Skip(5);
/// Kết quả là 3,6,7,2 và 0 Để lấy phần tử.
```
3. TakeWhile()

Trả về các phần tử từ tập hợp đã cho cho đến khi điều kiện được chỉ định là đúng. Nếu bản thân phần tử đầu tiên  không thỏa mãn điều kiện thì trả về một tập hợp rỗng.

> Public static IEnumerable <TSource> TakeWhile<TSource>(this IEnumerable <TSource>
source,Func<TSource,bool>,predicate);

```c#
int[] numbers = { 1, 5, 8, 4, 9, 3, 6, 7, 2, 0 };
var SkipFirstFiveElement = numbers.TakeWhile(n => n < 9);
/// Kết quả là 1,5,8 and 4.
```

4. SkipWhile()

Bỏ qua các phần tử dựa trên một điều kiện cho đến khi một phần tử không thỏa mãn điều kiện. Nếu bản thân phần tử đầu tiên không thỏa mãn điều kiện, thì nó sẽ bỏ qua 0 phần tử và trả về tất cả các phần tử trong dãy.

> Public static IEnumerable <TSource> SkipWhile<TSource>(this IEnumerable <TSource>
source,Func<TSource,bool>,predicate);

```c#
int[] numbers = { 1, 5, 8, 4, 9, 3, 6, 7, 2, 0 };
var SkipFirstFiveElement = numbers.SkipWhile(n => n < 9);
/// Kết quả là 9,3,6,7,2 and 0.
```

Dùng để làm gì . dùng để phân trang , tách dữ liệu chớ làm cái chi.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>