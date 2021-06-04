```c#
 public static class Base64Process
    {
        public static byte[] ToByteArray(this string value) =>
              Convert.FromBase64String(value);
    }
```