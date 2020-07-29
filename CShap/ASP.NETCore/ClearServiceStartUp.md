---------------------------------------------------------------
Chuyển  confing service ra 1 class để clear file startup
--------------------------------------------------------------
======>Tạo Mói Một Interface 
`public interface IInstaller
    {
        void InstallerServices(IServiceCollection services, IConfiguration configuration);
    }
`    
![image](https://user-images.githubusercontent.com/63473793/88827307-fec80180-d1f3-11ea-8cf6-fda1788875de.png)
---------------------------------------------------------------
======>Triển Khai interface
 `public class MVCInstaller : IInstaller
    {
        public void InstallerServices(IServiceCollection services, IConfiguration configuration)
        {
            services.AddControllersWithViews();
            services.AddSwaggerGen(x => {
                x.SwaggerDoc("v1", new Microsoft.OpenApi.Models.OpenApiInfo { Title = "Nam DZ", Version = "v1" });
            });
        }
    }
`
![image](https://user-images.githubusercontent.com/63473793/88827337-0b4c5a00-d1f4-11ea-9284-74ce7d890887.png)
--------------------------------------------------------------------------------
=============================> cài đặt vào startup
`
var settingService = typeof(Startup).Assembly.ExportedTypes.Where(x =>
                                                                                  typeof(IInstaller).IsAssignableFrom(x)
                                                                                  && !x.IsInterface
                                                                                  && !x.IsAbstract)
                                                                       .Select(Activator.CreateInstance)
                                                                       .Cast<IInstaller>()
                                                                       .ToList();
            settingService.ForEach(ins => ins.InstallerServices(services, Configuration));
`
![image](https://user-images.githubusercontent.com/63473793/88827274-f40d6c80-d1f3-11ea-8fe3-d9f4a1ba01d1.png)