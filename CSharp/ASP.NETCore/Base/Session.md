# mở đầu
```
Tôi đã từng được chỉ dẫn cách đây 1 năm 4/2020 là nếu một intern mà không phân biệt nổi session, cookie và cache thì ...... Nghe có thể hơi phũ phàng nhưng thật vậy. Tôi thấy đúng
```
## Session 
> session là cơ chế lưu trữ dữ liệu của server khi 1 client khi kết nối máy chủ hay là của phiên làm việc cho của ứng dụng. Nó giúp định hình luồng dữ liệu của client truy cập từ trang này qua trang khác. Biểu hiện rõ nhất chính là thông tin tài khoản. Để xác định được người dùng Server cần thông tin của người dùng (tài khoản mật khẩu). nếu như không có session thì mỗn lần đổi trang hay yêu cầu (request) thì lại phải đăng nhập lại rất tốn thời gian

Dữ liệu Session lưu trữ trên Server có thể là ở bộ nhớ Cache, có thể là ở CSDL SQLServer hoặc những nguồn lưu cache khác nhau. Ở đây tôi sẽ sử dụng bộ nhớ làm Storage lưu dữ liệu Session. Để ứng dụng sử dụng Session thêm vào dự án Package như sau:

```c#
Microsoft.AspNetCore.Session
Microsoft.Extensions.Caching.Memory
```

## Khởi động Session và Tích hợp Cookie
> để khởi động được cơ chế này 

1. ConfigureServices (Startup)
```c#
 services.AddDistributedMemoryCache(); // Đăng ký dịch vụ lưu cache trong bộ nhớ (Session sẽ sử dụng nó)
        services.AddSession(cfgS => {                 // Đăng ký dịch vụ Session
            cfgS.Cookie.Name = "Ses_Mid";             // lưu dữ liệu khôi phục tại cookie người dùng
            cfgS.IdleTimeout = new TimeSpan(0,30, 0); // Thời gian tồn tại của Session nếu như hết thời gian dù người dùng có Cookie thì phiên làm việc cũng sẽ không được khôi phục ở đây là 30 phút
         });
```

2. Configure (Startup)

```c#
  app.UseSession();   // đăng ký vào luồng hệ thống của .net core
```

> khi 1 request được gửi lên , dựa vào HttpContext mà chúng ta có một ISession  để làm việc 

## ISession và DistributedSession là gì 
> DistributedSession là một cách để bạn lưu trữ trạng thái phiên bên ngoài ứng dụng ASP.NET Core .Sử dụng Couchbase để lưu trữ trạng thái phiên có thể giúp bạn khi cần mở rộng quy mô trang web của mình, đặc biệt nếu bạn không muốn sử dụng các phiên cố định.


| Thành viên                      | Ý nghĩa                                                      |
|---------------------------------|--------------------------------------------------------------|
| ID                              | Thuộc tính lấy ID của Session, ID này có gửi về lưu ở Cookie |
| Clear()                         | Xóa bỏ các giá trị lưu trong Session                         |
| Set(String key, Byte[])         | Lưu mảng byte vào Session với key chỉ ra                     |
| TryGetValue(String key, Byte[]) | Lấy dữ liệu lưu trong key (trả về false là có thành công)    |
| SetString(String key, String s) | Lưu chuỗi vào key                                            |
| GetString(String key)           | Lấy chuỗi lưu trong key                                      |
| SetInt32(String key, Int32 val) | Lưu số kiểu int32 vào key                                    |
| GetInt32(String key)            | Lấy số int32 trong key                                       | 

# Luồng chạy
> Khởi tạo SessionMiddwere => lưu trữ dữ liệu vào session => lần truy vấn tiếp theo phục hồi theo ID session (thông thường server sẽ gửi cho client 1 đoạn cookie có chứa Id của phiên làm việc hiện tại căn cứ vào id đó mà Server hay nói chính xác là SessionMiddwere sẽ căn cứ vào cookei đó để phục hồi dữ liệu)
# Cách dùng
 ```c#
 HttpContext.Session.SetString("mysession", "mySessionValue");
 ```
# Lib common căn bản

```c#
public static class SessionExtensions
{
    public static void Set<T>(this ISession session, string key, T value)
    {
        session.Set(key, JsonSerializer.SerializeToUtf8Bytes(value));
    }

    public static T Get<T>(this ISession session, string key)
    {
        var value = session.Get(key);

        return value == null ? default(T) : 
            JsonSerializer.Deserialize<T>(value);
    }
}
```
> đây mới chỉ là cơ bản chưa có một chút gì là nâng cao. tối ưu hóa ...... 
> để phân biệt đk Sess , cook , cache phải hiểu từng thằng nó làm gì