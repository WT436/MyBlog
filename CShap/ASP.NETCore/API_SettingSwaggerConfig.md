Api ??????
Thường chúng ta thấy  khi ai đó viết api họ  thường có postman hay fiddler 4 ..... , 
nhưng có một cách hay ho hơn nhiều Swagger , trực tiếp luôn ,dài dòng quá ,nó đây nè 

![image](https://user-images.githubusercontent.com/63473793/88499681-c906fb00-cff0-11ea-900d-b1817660311c.png)

----------------------------------------------------------------------------------------------------------------
 Cài đặt thôi , demo .net nhé

 NUGET Swashbuckle.AspNetCore
 ![image](https://user-images.githubusercontent.com/63473793/88499225-724cf180-cfef-11ea-9ba8-47bfd6810890.png)
 ----------------------------------------------------------------------------------------------------------------
 Json :
 "SwaggerConfigStartup": {
   "JsonRoute": "swagger/{documentName}/swagger.json",
   "Description": "Nam API",
   "UIEndpoint": "v1/swagger.json"
   },  
 ![image](https://user-images.githubusercontent.com/63473793/88499278-927cb080-cfef-11ea-8e55-0f1347b6c40a.png)
 ----------------------------------------------------------------------------------------------------------------
 Class:public class SwaggerConfigStartup
     {
        public string JsonRoute { get; set; }
         public string Description { get; set; }
         public string UIEndpoint { get; set; }             
     }
 ![image](https://user-images.githubusercontent.com/63473793/88499353-c6f06c80-cfef-11ea-8e92-b48f8ba5a611.png)
 ----------------------------------------------------------------------------------------------------------------
 Controller =>
    [HttpGet("/api/nam")]
         public IActionResult get()
         {
             return Ok(new { name = "Nam" });
         }
 ![image](https://user-images.githubusercontent.com/63473793/88499299-9f010900-cfef-11ea-9286-d81162dbf8cf.png)
 ----------------------------------------------------------------------------------------------------------------
 Startup => services.AddSwaggerGen(x => {
                 x.SwaggerDoc("v1", new Microsoft.OpenApi.Models.OpenApiInfo{ Title = "Nam DZ", Version = "v1" });
             });
              var swaggerConfigStartup = new SwaggerConfigStartup();
             Configuration.GetSection(nameof(SwaggerConfigStartup)).Bind(swaggerConfigStartup);
 
             app.UseSwagger(op => { op.RouteTemplate = swaggerConfigStartup.JsonRoute; });
              app.UseSwaggerUI(op =>
            {
                 op.SwaggerEndpoint(swaggerConfigStartup.UIEndpoint, swaggerConfigStartup.Description);
             });
 ![image](https://user-images.githubusercontent.com/63473793/88499326-b0e2ac00-cfef-11ea-8461-f5c4e0085a88.png)
