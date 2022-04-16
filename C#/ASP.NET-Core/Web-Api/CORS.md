# CORS

CORS là viết tắt của Cross-Origin Resource Sharing.

CORS là một cơ chế cho phép nhiều tài nguyên khác nhau (fonts, Javascript, v.v…) của một trang web có thể được truy vấn từ domain khác với domain của trang đó. CORS là viết tắt của từ Cross-origin resource sharing.

## Why ?

Bởi vì bảo mật của trình duyệt ngăn một trang web thực hiện các yêu cầu ajax đến một domain khác. Hạn chế này được gọi là chính sách cùng nguồn gốc và ngăn một trang web độc hại đọc dữ liệu nhạy cảm từ một trang web khác.

Nhưng điều gì sẽ xảy ra nếu chúng tôi muốn cho phép các domain khác truy cập vào các API của chúng tôi?

Ví dụ như chúng ta có 2 trang web :

```
http://wekee.vn/abc
http://wekee.vn/xyz
```

Dễ thấy 2 trang web trên có chung 1 root là http://wekee.vn

nhưng bây giờ chúng ta có một chút thay đổi như sau. Chủ yếu là các subdomain và các trang web dùng để support cho trang chính.

```
http://domain.in //// chết thật chúng ta cần một tên domain hỗ trợ
http://www.domain.vn/xyz.html //// chết tiệt chúng ta cần tên domain phụ!
http://domain.vn:7000/abc.html //// Đậu xanh . chúng ta cần nhiều cổng để phục vụ mục đính khác nhau.
```

Nếu CORS không được bật, bạn có thể gặp một ngoại lệ như trường hợp bên dưới khi cố gắng truy cập vào một domain khác bằng lệnh gọi ajax:

```
XMLHttpRequest cannot load http://www.wekee.vn/. No 'Access-Control-Allow-Origin' header is present on the requested resource.
```

Chúng ta sẽ có ty tỷ các câu hỏi được đặt ra như sau :

- Nhưng điều gì sẽ xảy ra nếu chúng tôi muốn cho phép các domain khác truy cập vào các API của chúng tôi?

Theo tài liệu ASP.NET Core, "CORS là một tiêu chuẩn W3C cho phép server nới lỏng chính sách cùng nguồn gốc. Sử dụng CORS, server có thể cho phép rõ ràng một số yêu cầu có cross-origin trong khi từ chối các yêu cầu khác". Nói một cách đơn giản - CORS cung cấp cho bạn sức mạnh để cho phép các cuộc gọi giữa nhiều domain từ các domain được chỉ định.

## Vậy CORS hoạt động như thế nào?

- Khi chúng ta sử dụng CORS, các HTTP headers mới được giới thiệu cho phép các yêu cầu có cross-origin.
- "Nếu trình duyệt hỗ trợ CORS, trình duyệt sẽ tự động đặt các headers đó cho các yêu cầu có cross-origin."
- Sau đó, các yêu cầu cross-origin này được gửi đến server có chứa headers gốc bao gồm thông tin domain.
- Nếu mọi thứ diễn ra tốt đẹp với server, server sẽ thêm headers Access-Control-Allow-Origin trong phản hồi.
- Giá trị của headers , Access-Control-Allow-Origin, có thể là \* trong trường hợp cho phép bất kỳ nguồn gốc nào hoặc khi chúng tôi muốn cho phép bất kỳ domain cụ thể nào trong tên domain, tức là Access-Control-Allow-Origin: http://wekee.vn
- Nếu phản hồi không bao gồm headers Access-Control-Allow-Origin, yêu cầu không thành công.

## WOW vậy .net CORE có hỗ trợ CORS không?

Oh rất tiếc. không! nó không chỉ hỗ trợ mà còn hỗ trợ mạnh là đàng khác và lại rất dễ sử dụng.

Bạn chỉ cần làm theo các bước sau:

- Cài đặt gói Microsoft.AspNetCore.Cors Nuget.
- Định cấu hình CORS trong phương thức ConfigureService.
- Enable CORS sử dụng middleware trong file startup => Configure method.
- Enable CORS trong .NET Core MVC bằng cách bật nó trong Controllers hoặc actions hoặc globally.

Ok chúng ta bắt đầu config :

1. Cài đặt :

![image](https://user-images.githubusercontent.com/63473793/123515399-6d8e3300-d6c1-11eb-8604-4e663f9c9a82.png)

2. Khởi tạo

```c#
public void ConfigureServices(IServiceCollection services)
{
    services.AddCors(options =>
    {
        options.AddPolicy("AllowMyOrigin",
        builder => builder.WithOrigins("http://wekee.vn"));
    });
}
```

Có khá nhiều phương thức hỗ trợ . chúng được liệt kê ngay bên dưới đây :

- AllowAnyOrigin () - Cho phép bất kỳ nguồn gốc nào.
- AllowAnyHeader () - Cho phép tất cả các tiêu đề HTTP trong yêu cầu.
- WithHeaders () - Chỉ cho phép các tiêu đề cụ thể.
- AllowAnyMethod () -Cho phép tất cả các phương thức HTTP.
- WithMethods () - Chỉ cho phép các phương thức HTTP cụ thể.
- AllowCredentials () - Thông tin xác thực được chuyển với yêu cầu nguồn gốc chéo, chủ yếu được sử dụng để xác thực cookie và HTTP.

3. Đăng ký

- Bật toàn bộ ứng dụng
```c#
public void Configure(IApplicationBuilder app)
{
    app.UseCors("AllowMyOrigin");
}
```
- Bật theo thành phần 

    * Controller's Action
    ```c#
    [EnableCors("AllowMyOrigin")]
    public IEnumerable<string> Get()
    {
        return new string[] { "value1", "value2" };
    }    
    ```

    * Controller
    ```c#
    [EnableCors("AllowMyOrigin")]
    public class ValuesController : Controller
    ```

    * Globally cái này thì phải dùng đến filter nên sẽ có một bài về filter sau
    ```c#
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<MvcOptions>(options =>
        {
            options.Filters.Add(new CorsAuthorizationFilterFactory("AllowMyOrigin"));
        });
    }
    ```

Hôm nay đến đây thôi. goodbye!

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>