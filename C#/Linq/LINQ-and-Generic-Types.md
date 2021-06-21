# LINQ and Generic Types (C#)
- nguồn : https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/linq-and-generic-types

- Khái niệm : LINQ (Language Integrated Query, tạm dịch là ngôn ngữ truy vấn tích hợp) đưa ra 1 mô hình bền vững để hoạt động với các dạng 
    nguồn dữ liệu và định dạng dữ liệu khác nhau. Trong LINQ, bạn phải làm quen với chuyện làm việc với các đối tượng (objects). LINQ cho phép 
    dùng các đoạn code đơn giản để truy vấn và chuyển đổi dữ liệu trong các tài liệu XML, cơ sở dữ liệu SQL, tập dữ liệu ADO.NET, các tập hợp .
    NET, và bất kỳ định dạng nào mà LINQ provider hỗ trợ.
- IEnumerable<T> Trong Linq
```c#
IEnumerable<Customer> customerQuery =
    from cust in customers
    where cust.City == "London"
    select cust;

foreach (Customer customer in customerQuery)
{
    Console.WriteLine(customer.LastName + ", " + customer.FirstName);
}
/*
Biến truy vấn của linq là một kiểu IEnumerable<T> hoặc là IQueryable<T> khi nào chúng ta thực thi thì chúng ta sẽ dùng IEnumerable<Customer> 
Sử dụng nó như một 
*/
```
