-- Dtos
```c#
public class ExternalClientJsonConfiguration
    {
        public string Issuer { get; set; }
        public string Audience { get; set; }
        public string RsaPrivateKey { get; set; }
        public string RsaPublicKey { get; set; }
    }


 public class JwtCustomClaims
    {
        /// <summary>
        /// Id của tài khoản
        /// </summary>
        public int Id { get; set; }
        /// <summary>
        /// Tên tài khoản
        /// </summary>
        public string Account_User { get; set; } 
        /// <summary>
        /// Email của tài khoản
        /// </summary>
        public string Email { get; set; }
        /// <summary>
        /// Ip của tài khoản
        /// </summary>
        public string Ip { get; set; }
    }

 public class JwtResponse
    {
        public string Token { get; set; }
        public long ExpiresAt { get; set; }
    }
```
-- class
```c#
public interface IJwtHandler
    {
        JwtResponse CreateToken(JwtCustomClaims claims);
        JwtCustomClaims ReadFullInfomation(string token);
    }

  public class JwtHandler : IJwtHandler
    {
        private readonly ExternalClientJsonConfiguration _settings;
        public JwtHandler(IOptions<ExternalClientJsonConfiguration> setting)
        {
            _settings = setting.Value;
        }

        public JwtResponse CreateToken(JwtCustomClaims claims)
        {
            var privateKey = _settings.RsaPrivateKey;

            using RSA rsa = RSA.Create();
            var derArray = Convert.FromBase64String(privateKey);
            rsa.ImportRSAPrivateKey(derArray, out _);

            var signingCredentials = new SigningCredentials(new RsaSecurityKey(rsa), SecurityAlgorithms.RsaSha256)
            {
                CryptoProviderFactory = new CryptoProviderFactory { CacheSignatureProviders = false }
            };

            var now = DateTime.Now;
            var unixTimeSeconds = new DateTimeOffset(now).ToUnixTimeSeconds();

            var jwt = new JwtSecurityToken(
                audience: _settings.Audience,
                issuer: _settings.Issuer,
                claims: new Claim[] {
                    new Claim(JwtRegisteredClaimNames.Iat, unixTimeSeconds.ToString(), ClaimValueTypes.Integer64),
                    new Claim(JwtRegisteredClaimNames.Jti, Guid.NewGuid().ToString()),
                    new Claim(nameof(claims.Id),claims.Id.ToString()),
                    new Claim(nameof(claims.Account_User),claims.Account_User.ToString()),
                    new Claim(nameof(claims.Email),claims.Email.ToString()),
                    new Claim(nameof(claims.Ip),claims.Ip.ToString())
                },
                notBefore: now,
                expires: now.AddDays(30),
                signingCredentials: signingCredentials
            );

            string token = new JwtSecurityTokenHandler().WriteToken(jwt);

            return new JwtResponse
            {
                Token = token,
                ExpiresAt = unixTimeSeconds,
            };
        }

        private bool ValidateToken(string token)
        {
            var publicKey = _settings.RsaPublicKey;

            using RSA rsa = RSA.Create();
            var derArray = Convert.FromBase64String(publicKey);
            rsa.ImportRSAPublicKey(derArray, out _);

            var validationParameters = new TokenValidationParameters
            {
                ValidateIssuer = true,
                ValidateAudience = true,
                ValidateLifetime = true,
                ValidateIssuerSigningKey = true,
                ValidIssuer = _settings.Issuer,
                ValidAudience = _settings.Audience,
                IssuerSigningKey = new RsaSecurityKey(rsa),

                CryptoProviderFactory = new CryptoProviderFactory()
                {
                    CacheSignatureProviders = false
                }
            };

            try
            {
                var handler = new JwtSecurityTokenHandler();
                handler.ValidateToken(token, validationParameters, out var validatedSecurityToken);
            }
            catch
            {
                return false;
            }

            return true;
        }

        public JwtCustomClaims ReadFullInfomation(string token)
        {
            JwtCustomClaims infoToken = new JwtCustomClaims();
            if (!string.IsNullOrEmpty(token) && ValidateToken(token))
            {
                var tokenHandler = new JwtSecurityTokenHandler();
                var securityToken = tokenHandler.ReadToken(token) as JwtSecurityToken;

                infoToken.Id = Convert.ToInt32(securityToken.Claims.First(claim => claim.Type == nameof(infoToken.Id)).Value);
                infoToken.Account_User = securityToken.Claims.First(claim => claim.Type == nameof(infoToken.Account_User)).Value;
                infoToken.Email = securityToken.Claims.First(claim => claim.Type == nameof(infoToken.Email)).Value;
                infoToken.Ip = securityToken.Claims.First(claim => claim.Type == nameof(infoToken.Ip)).Value;
            }
            return infoToken;
        }
    }

 public class TokenAuth
    {
        #region Create a token
        /// <summary>
        /// lấy thông tin tài khoản và khởi tạo token 
        /// </summary>
        /// <returns></returns>
        public string GenerateToken(JwtCustomClaims infoToken)
        {
            var tokenHandler = new JwtSecurityTokenHandler();
            var tokenDescriptor = new SecurityTokenDescriptor
            {
                Subject = new ClaimsIdentity(new Claim[]
                {
                    new Claim("Id",infoToken.Id.ToString()),
                    new Claim("Account_User",infoToken.Account_User.ToString()),
                    new Claim("Email",infoToken.Email.ToString()),
                    new Claim("Ip",infoToken.Ip.ToString()),
                }),
                Expires = DateTime.UtcNow.AddDays(1),
                Issuer = "https://localhost:44306/",
                Audience = "https://localhost:44306/",
                SigningCredentials = new SigningCredentials(
                    new SymmetricSecurityKey(Encoding.ASCII.GetBytes("0159c0ca-c966-4410-8650-7fbb4e535513")),
                    SecurityAlgorithms.HmacSha256Signature)
            };

            var token = tokenHandler.CreateToken(tokenDescriptor);
            return tokenHandler.WriteToken(token);
        }
        #endregion

        #region Validating A Token
        /// <summary>
        /// 
        /// </summary>
        /// <param name="token"></param>
        /// <returns></returns>
        public bool ValidateCurrentToken(string token)
        {
            var mySecret = "0159c0ca-c966-4410-8650-7fbb4e535513";
            var mySecurityKey = new SymmetricSecurityKey(Encoding.ASCII.GetBytes(mySecret));

            var myIssuer = "https://localhost:44306/";
            var myAudience = "https://localhost:44306/";

            var tokenHandler = new JwtSecurityTokenHandler();
            try
            {
                tokenHandler.ValidateToken(token, new TokenValidationParameters
                {
                    ValidateIssuerSigningKey = true,
                    ValidateIssuer = true,
                    ValidateAudience = true,
                    ValidIssuer = myIssuer,
                    ValidAudience = myAudience,
                    IssuerSigningKey = mySecurityKey
                }, out SecurityToken validatedToken);
            }
            catch
            {
                return false;
            }
            return true;
        }
        #endregion

        #region Read claims
        /// <summary>
        /// 
        /// </summary>
        /// <param name="token"></param>
        /// <param name="claimType"></param>
        /// <returns></returns>
        public string GetClaim(string token, string claimType)
        {
            var tokenHandler = new JwtSecurityTokenHandler();
            var securityToken = tokenHandler.ReadToken(token) as JwtSecurityToken;

            var stringClaimValue = securityToken.Claims.First(claim => claim.Type == claimType).Value;
            return stringClaimValue;
        }
        #endregion
      
    }
```
-- cách dùng 

```c#
private static IJwtHandler _jwtHandler;
private static IOptions<ExternalClientJsonConfiguration> options;
private static readonly ExternalClientJsonConfiguration externalClientJsonConfiguration = new ExternalClientJsonConfiguration();

_jwtHandler = new JwtHandler(options);
```