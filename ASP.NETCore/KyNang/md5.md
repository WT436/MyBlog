```c#
 public static class MD5
    {
        public static string Random()
        {
            return new Random().Next(100000, 999999).ToString();
        }
        public static string MD5Hash(string input, string hashPass)
        {
            StringBuilder hash = new StringBuilder();
            MD5CryptoServiceProvider md5provider = new MD5CryptoServiceProvider();
            string passString = (input + hashPass).Trim().ToString();
            byte[] bytes = md5provider.ComputeHash(new UTF8Encoding().GetBytes(passString));

            for (int i = 0; i < bytes.Length; i++)
            {
                hash.Append(bytes[i].ToString("x2"));
            }
            return hash.ToString();
        }
    }
```
