# Action Selectors & Action Verbs in ASP.NET Core

## Action Name

- Thuộc tính ActionName xác định tên của hành động . Công cụ routing sẽ sử dụng tên này thay vì tên phương thức để khớp với phân đoạn định tuyến tên hành động. Bạn sẽ sử dụng thuộc tính này khi bạn muốn đặt bí danh cho action name.

```c#
[ActionName("HaiNam")]
public string Edit()
{
    return "XinChaoHaiNam";
}
```

- Tên hành động cho hành động Edit được thay đổi thành HaiNam bằng cách sử dụng thuộc tính ActionName.
- chúng ta cx có thể sử dụng

```c#
[Route("HaiNam")]
//hoặc
[httpget("HaiNam")]
```

## Non Action

- Các phương thức public trong lớp controller được gọi là các phương thức Action. Bất kỳ ai ở bất kỳ đâu trên thế giới đều có thể sử dụng các phương thức này bằng cách chỉ cần gõ URL vào trình duyệt.
- Bạn có thể cho Routing Engine biết rằng một phương thức cụ thể không phải là một phương thức Action bằng cách trang trí nó bằng thuộc tính NonAction như được hiển thị bên dưới

```c#


4
5
6
7
8
9
10

public class HomeController : Controller
{
    [NonAction]
    public string Nam()
    {
        return "Hello from Hainam";
    }
}
```

## Action Verbs

- Bộ chọn Action được sử dụng khi bạn muốn kiểm soát phương thức Action dựa trên phương thức yêu cầu HTTP. Điều này được thực hiện bằng cách sử dụng tập hợp các thuộc tính do MVC cung cấp, chẳng hạn như các thuộc tính HttpGet và HttpPost, được gọi chung là Thuộc tính HTTP.
- Có một số động từ HTTP có sẵn để được sử dụng trong các ứng dụng cốt lõi của ASP.NET. Đó là GET, POST, PUT, DELETE, HEAD, OPTIONS, PATCH. Mỗi động từ này có các Thuộc tính Phương thức HTTP được liên kết được xác định trong
- có 9 loại thì phải

## AcceptVerbs

- Thuộc tính HTTP AcceptVerbs cho phép sử dụng nhiều động từ hành động trên một Phương thức hành động.

```c#
[AcceptVerbs(HttpVerbs.Get | HttpVerbs.Post)]
public ActionResult AboutUs()
{
    return View();
}
```
