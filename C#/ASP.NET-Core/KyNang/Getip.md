```c#
 /*Get IpClient bên DI*/
           services.AddControllersWithViews();
           services.AddSingleton<IActionContextAccessor, ActionContextAccessor>();
//trong contronler
    private readonly IActionContextAccessor _GetIP;
    public namController( IActionContextAccessor GetIP)
        {
            _GetIP = GetIP;
        }

    var ip = _GetIP.ActionContext.HttpContext.Connection.RemoteIpAddress.ToString();
```

```c#
var ip = HttpContext.Connection.RemoteIpAddress.ToString();
```

lưu ý là nếu trên https://localhost thì nó sẽ trả về 0.0.0.1