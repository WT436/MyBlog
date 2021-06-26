```c#
public class IdentityController : Controller
    {
        private readonly IIdentitiService _identitiService;
        public IdentityController(IIdentitiService identitiService)
        {
            _identitiService = identitiService;
        }

        [HttpPost]
        [Route("api/v1/identity/login")]
        public async Task<IActionResult> Reg([FromBody] UserRegRequest userRegRequest)
        {
            var au = await _identitiService.AuThenticationResultAsync(userRegRequest.Email, userRegRequest.Password);
            if(!au.success)
            {
                return BadRequest(new AuthenFailedResponses
                {
                    Error = au.Error
                });
            }
            return Ok(new RegistrationResponse
            {
                token = au.token
            });
        }
    }
```
![image](https://user-images.githubusercontent.com/63473793/89026970-d525ec00-d353-11ea-85c6-9bd3efd52806.png)
```c#
    public interface IIdentitiService
    {
        Task<AuThenticationResult> AuThenticationResultAsync(string email, string pass);
    }
```
![image](https://user-images.githubusercontent.com/63473793/89027204-4bc2e980-d354-11ea-8026-0a33fb29ccc0.png)
```c#
services.AddScoped<IIdentitiService, IdentitiService>();
```
![image](https://user-images.githubusercontent.com/63473793/89027307-7745d400-d354-11ea-817e-c549955f0bf7.png)
```c#
    public class AuthenFailedResponses
    {
        public IEnumerable<string> Error { get; set; }
    }
```
![image](https://user-images.githubusercontent.com/63473793/89027334-82006900-d354-11ea-9814-cf07e5d0730a.png)
```c#
public class AuThenticationResult
    {   
        public string token { get; set; }
        public bool success { get; set; }
        public IEnumerable<string> Error { get; set; }
    }
```
![image](https://user-images.githubusercontent.com/63473793/89027356-8c226780-d354-11ea-82c7-c94e94b3ea6e.png)
```c#
public class RegistrationResponse
    {
        public string token { get; set; }
    }   
```
![image](https://user-images.githubusercontent.com/63473793/89027376-95abcf80-d354-11ea-8be8-87c13c12c4a8.png)
```c#
    public class UserRegRequest
    {
        public string Email { get; set; }
        public string Password { get; set; }
    }
```
![image](https://user-images.githubusercontent.com/63473793/89027392-9e040a80-d354-11ea-9fab-2ae25b77da88.png)
```c#
 public class IdentitiService : IIdentitiService
    {
        //private readonly UserManager<IdentityUser> _UserManager;
        private readonly JwtSettings _jwtsetting;
        public IdentitiService(/*UserManager<IdentityUser> UserManager,*/ JwtSettings jwtsetting)
        {
            //_UserManager = UserManager;
            _jwtsetting = jwtsetting;
        }
        public async Task<AuThenticationResult> AuThenticationResultAsync(string email, string pass)
        {
            //var exuser = await _UserManager.FindByEmailAsync(email);
            if (email == null)
            {
                return new AuThenticationResult
                {
                    Error = new[] { "Dia chi Email Ton tai" }
                };
            }

            var newUser = new IdentityUser
            {
                Email = email,
                UserName = email
            };
            //var create = await _UserManager.CreateAsync(newUser, pass);
            var a = true;
            if (/*!create.Succeeded*/ !a)
            {
                return new AuThenticationResult
                {
                    Error = /*create.Errors.Select(x => x.Description)*/ new[] { "Dia chi  Ton tai" }
                };
            }

            var tokenhan = new JwtSecurityTokenHandler();

            var key = Encoding.ASCII.GetBytes(_jwtsetting.Secret);
            var tokenDescriptor = new SecurityTokenDescriptor {
                Subject = new ClaimsIdentity(new[] {
                    new Claim(JwtRegisteredClaimNames.Sub, newUser.Email),
                    new Claim(JwtRegisteredClaimNames.Email, newUser.Email),
                    new Claim("id", newUser.Id),
                    new Claim(JwtRegisteredClaimNames.Jti, Guid.NewGuid().ToString()),
                }),
                Expires = DateTime.UtcNow.AddHours(2),
                SigningCredentials = new SigningCredentials(new SymmetricSecurityKey(key),SecurityAlgorithms.HmacSha256Signature)
            };

            var token = tokenhan.CreateToken(tokenDescriptor);

            return new AuThenticationResult
            {
                success = true,
                token = tokenhan.WriteToken(token)
            };
        }
    }
}
```
![image](https://user-images.githubusercontent.com/63473793/89027439-b542f800-d354-11ea-8842-cd5acee0f597.png)
![image](https://user-images.githubusercontent.com/63473793/89027479-c68c0480-d354-11ea-875e-ca2244e041d1.png)
![image](https://user-images.githubusercontent.com/63473793/89027517-d7d51100-d354-11ea-9d77-9d964c4fbf5d.png)
