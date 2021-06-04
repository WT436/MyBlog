```c#
 app.UseMvc(routes =>
            {
                routes.MapRoute(
                        name: "AccountAreas",
                        template: "{controller=LoginAccount}/{action=Index}/{id?}",
                 new string[] { "Wekee.API.Src.AccountAreas" });

                routes.MapRoute(
                       name: "HomeAreas",
                       template: "{controller=HomePage}/{action=Index}/{id?}",
                new string[] { "Wekee.API.Src.HomeAreas" });

                routes.MapRoute(
                        name: "Default",
                        template: "{controller=Invalid}/{action=Index}/{id?}",
                 new string[] { "Wekee.API.Src.Controllers" });
            });
```