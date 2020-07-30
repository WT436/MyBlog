# Authentication là Gì

- Authentication là về việc xác thực thông tin đăng nhập của bạn như Tên người dùng / ID người dùng và mật khẩu để xác minh danh tính của bạn. Trong các public và private network, hệ thống xác thực danh tính người dùng thông qua mật khẩu đăng nhập. Authentication thường được thực hiện bởi tên người dùng và mật khẩu, và đôi khi kết hợp với các yếu tố xác thực, trong đó đề cập đến các cách khác nhau để được xác thực.

Các Authentication factor xác định các yếu tố khác nhau mà hệ thống sử dụng để xác minh một danh tính trước khi cấp cho anh ta quyền truy cập vào bất cứ điều gì từ việc truy cập file đến yêu cầu giao dịch ngân hàng. Một danh tính người dùng có thể được xác định bởi những gì anh ta biết, những gì anh ta có. Khi nói đến bảo mật, ít nhất hai hoặc cả ba yếu tố xác thực phải được xác minh để cấp cho ai đó quyền truy cập vào hệ thống.

Dựa trên cấp độ bảo mật, authentication factor có thể thay đổi theo một trong các cách sau:

- Single-Factor Authentication – Nó là phương thức xác thực đơn giản nhất thường dựa vào mật khẩu đơn giản để cấp cho người dùng quyền truy cập vào một hệ thống cụ thể là một website hoặc network. Người này có thể yêu cầu quyền truy cập vào hệ thống chỉ bằng một trong các thông tin đăng nhập để xác minh danh tính của mình. Ví dụ phổ biến nhất về xác thực một yếu tố sẽ là thông tin đăng nhập chỉ yêu cầu mật khẩu đối với tên người dùng hoặc địa chỉ email.
- Two-Factor Authentication – Như tên của nó, nó có một quy trình xác minh gồm hai bước, không chỉ yêu cầu tên người dùng và mật khẩu, mà còn một thứ mà chỉ người dùng biết, để đảm bảo mức độ bảo mật bổ sung, chẳng hạn như pin ATM, chỉ người dùng mới biết. Sử dụng tên người dùng và mật khẩu cùng với một thông tin bí mật bổ sung khiến cho những kẻ lừa đảo hầu như không thể đánh cắp dữ liệu có giá trị.
- Multi-Factor Authentication – Nó có một phương thức xác thực tiên tiến nhất sử dụng hai hoặc nhiều mức bảo mật từ các loại xác thực độc lập để cấp quyền truy cập cho người dùng vào hệ thống. Tất cả các yếu tố phải độc lập với nhau để loại bỏ bất kỳ lỗ hổng nào trong hệ thống. Các tổ chức tài chính, ngân hàng và các cơ quan thực thi pháp luật sử dụng xác thực nhiều yếu tố để bảo vệ dữ liệu và ứng dụng của họ khỏi các mối đe dọa tiềm ẩn.

Ví dụ: khi bạn nhập thẻ ATM vào máy ATM, máy sẽ yêu cầu bạn nhập mã pin. Sau khi bạn nhập mã pin chính xác, ngân hàng sẽ xác nhận danh tính của bạn rằng thẻ thực sự thuộc về bạn và bạn là chủ sở hữu hợp pháp của thẻ. Bằng cách xác nhận mã pin thẻ ATM của bạn, ngân hàng thực sự xác minh được danh tính của bạn, được gọi là authentication. Nó chỉ đơn thuần xác định bạn là ai, không có gì khác.
Nguồn : https://topdev.vn/blog/authentication-vs-authorization/

# Giao Diện

![image](https://user-images.githubusercontent.com/63473793/88982242-f524c380-d2f1-11ea-98c6-ba06e95db115.png)

# Json

![image](https://user-images.githubusercontent.com/63473793/88982273-079efd00-d2f2-11ea-91ae-b00de341eddf.png)

```C#
"JwtSettings": {
    "Secret": "namnamnamnamnamnamnamnamnamnamV1" //Nên có 32 Ký tự
  },
```

# Class

![image](https://user-images.githubusercontent.com/63473793/88982286-0ff73800-d2f2-11ea-9251-f11d2c095178.png)

```C#
 public class JwtSettings//tên class và hàm nên trùng với Tên Trong Json
    {
        public string Secret { get; set; }
    }
```

# services

![image](https://user-images.githubusercontent.com/63473793/88982323-27cebc00-d2f2-11ea-9f6c-27204c2ee195.png)

```C#
var jwtSettings = new JwtSettings();//dat ten theo class nhưng là in thường nếu ko sẽ lỗi
            configuration.Bind(nameof(jwtSettings), jwtSettings);
            services.AddSingleton(jwtSettings);//lấy dữ liệu từ Json Đẩy Vào class

            services.AddAuthentication(x =>
            {
                x.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
                //using Microsoft.AspNetCore.Authentication.JwtBearer; đây là thư viện cài đặt nó vào
                x.DefaultScheme = JwtBearerDefaults.AuthenticationScheme;
                x.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
            })
                .AddJwtBearer(x =>
                {
                    x.SaveToken = true;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters
                    {
                        ValidateIssuerSigningKey = true,
                        IssuerSigningKey = new SymmetricSecurityKey(Encoding.ASCII.GetBytes(jwtSettings.Secret)),
                        ValidateIssuer = false,
                        ValidateAudience = false,
                        RequireExpirationTime = false,
                        ValidateLifetime = true
                    };
                });
```

# SwaggerGen

![image](https://user-images.githubusercontent.com/63473793/88982360-403ed680-d2f2-11ea-98b9-a559a791338a.png)

```C#
 //add vao cho Swagger giao dien
                var secu = new Dictionary<string, IEnumerable<string>> {
                    {"NamDepTrai", new string[0]}
                };

                x.AddSecurityDefinition(name: "NamDepTrai", new OpenApiSecurityScheme()
                {
                    Description = "JWT Authorization NamDZ",
                    Name = "Authorization",
                    In = ParameterLocation.Header,
                    Type = SecuritySchemeType.ApiKey
                });
                x.AddSecurityRequirement(new OpenApiSecurityRequirement
                {
                    {new OpenApiSecurityScheme{Reference = new OpenApiReference
                    {
                        Id = "NamDepTrai",
                        Type = ReferenceType.SecurityScheme
                    }}, new List<string>()}
                });

```

# StartUp

![image](https://user-images.githubusercontent.com/63473793/88982383-52207980-d2f2-11ea-9505-18510568dfe2.png)

```C#
 app.UseAuthentication();
```
