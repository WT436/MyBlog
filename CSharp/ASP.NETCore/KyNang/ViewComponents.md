# ViewComponent

## quên partial view đi , đây mới là thứ chúng ta cần ( ahihi cái nào cx có mạnh yếu tùy cơ ứng biến )

- nó tương tự như partial view ,nhưng chúng mạnh hơn nhiều , wow
- View components : không sử dụng liên kết mô hình và chỉ phụ thuộc vào dữ liệu được cung cấp khi gọi vào nó
- nó được tạo nên từ view và cotroller , nhuwng nos lamf vieecj voiws Razor Pages

1. View components

- Hiển thị một đoạn thay vì toàn bộ phản hồi.
- Bao gồm các lợi ích phân tách các mối quan tâm và khả năng kiểm tra giống nhau được tìm thấy giữa controller và view
- Có thể có các tham số và logic nghiệp vụ.
- Thường được gọi từ một trang bố cục.

2. tutorial

- Cài đặt

```c#
services.AddMvc()
/*setting trong start up nó thật cái quần què này tỗi cx chưa dùng */
    .AddRazorOptions(options =>
    {
        options.ViewLocationFormats.Add("/{0}.cshtml");
    })
    .SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
```

- tạo cotroller

```console
đầu tiên  thêm một thư mục ViewComponents ngang cấp với  areas
tạo một class MenuViewComponent  nhớ phải có hậu tố ViewComponent
```

```c#
// nó tương tự ntn
public class MenuViewComponent: ViewComponent
    {
        public async Task<IViewComponentResult> InvokeAsync()
        {
            ViewData["Nam"] = "Nam";
            return View();
        }
    }
```

```console
sau đó chúng ta add 1  thư mục Components vào thư mục Shared
trong Components ta add tên ViewComponent ở đây là Menu
nhớ view mặc định của nó là Default.cshtml
vì chúng ta return View();
nếu muốn return vào 1 view mà chúng ta muốn thì return View("Tên view ");
vd return View("Index");
```

- trieenr khgai

```c#
@await Component.InvokeAsync("Menu") // không tham số

@await Component.InvokeAsync("Menu", new { thamso1 = 4, thamso2  = true })
// hoặc chúng ta có thể dùng Tag Helper
@addTagHelper *, MyWebApp
<vc:Tên-view tham-so-1="2" tham-so-2="false">
</vc:Tên-view>
// thôi dùng cái trên cho lành
```

- nhiều lần đau đầu vì muốn area cx có viewComponents nhưng nó không tìm thấy trang , vì đơn giản kho\i có 2 thứ nó không thể xác định chính xác cần thứ nào nên báo lỗi
- cú pháp đầy đủ của viewcomponent Controller

````c#
[ViewComponent(Name ="Menu")]
    public class MenuViewComponent: ViewComponent
    {
        public async Task<IViewComponentResult> InvokeAsync()//tham số truyền như bt
        {
            ViewData["Nam"] = "Nam";
            return View();
        }
    }
    ```
````
