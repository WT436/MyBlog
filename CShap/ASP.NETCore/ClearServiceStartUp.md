---------------------------------------------------------------
Chuyển  confing service ra 1 class để clear file startup
--------------------------------------------------------------

Tạo Mới Một Interface 

public interface IInstaller<br />
    {<br />
        void InstallerServices(IServiceCollection services, IConfiguration configuration);<br />
    }<br />
<br />   
![image](https://user-images.githubusercontent.com/63473793/88827307-fec80180-d1f3-11ea-8cf6-fda1788875de.png)

---------------------------------------------------------------

======>Triển Khai interface<br />

 public class MVCInstaller : IInstaller<br />
    {<br />
        public void InstallerServices(IServiceCollection services, IConfiguration configuration)<br />
        {<br />
            services.AddControllersWithViews();<br />
            services.AddSwaggerGen(x => {<br />
                x.SwaggerDoc("v1", new Microsoft.OpenApi.Models.OpenApiInfo { Title = "Nam DZ", Version = "v1" });<br />
            });<br />
        }<br />
    }<br />
<br />
![image](https://user-images.githubusercontent.com/63473793/88827337-0b4c5a00-d1f4-11ea-9284-74ce7d890887.png)<br />

--------------------------------------------------------------------------------

=============================> cài đặt vào startup<br />

var settingService = typeof(Startup).Assembly.ExportedTypes.Where(x =><br />
                                                                  typeof(IInstaller).IsAssignableFrom(x)<br />
                                                                  && !x.IsInterface<br />
                                                                  && !x.IsAbstract)<br />
                                                           .Select(Activator.CreateInstance)<br />
                                                           .Cast<IInstaller>()<br />
                                                           .ToList();<br />
            settingService.ForEach(ins => ins.InstallerServices(services, Configuration));<br />

![image](https://user-images.githubusercontent.com/63473793/88827274-f40d6c80-d1f3-11ea-8fe3-d9f4a1ba01d1.png)
