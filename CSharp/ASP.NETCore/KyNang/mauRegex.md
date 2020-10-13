```c#
 public static class MauRegex
    {
        public static string KT1 = "[+=`!#$%&*()'\":;<>?]";//kiem tra ky tu dac  biet
        public static string KT2 = "[0-9]{1,}";// kiem tra so it nhat 1
        public static string KT3 = "[a-z]{1,}";//kiểm tra ký tự thường xuất hiện  2 lần trở lên
        public static string KT4 = ".{8,}";//so luong ky tu can co
        public static string KT5 = "[A-Z]{1,}";//ky tu in hoa phai co mot
        public static string KT6 = "[a-zA-Z0-9]{0,}([.]?[a-zA-Z0-9]{1,})[@](gmail.com)"; //test gamil
        public static string KT7 = "[+=`!#$%&*()'\":;<>?]";
        public static string KT8 = @" ^[-+]?[0 - 9] *\.?[0-9]+$";
        public static string KT9 = "^.{0,10}$";// co 10 ky tu
        public static string KT10 = "[+`!#$%&*()'\":;<>,?]";
        public static string KT11 = "^[^\\s]+$";//khoảng trắng
        public static string KT12 = "[A-Z]{1,}";
        public static string KT13 = "";
        public static string KT14 = "";
        public static string KT15 = "";
        public static string KT16 = "";
        public static string KT17 = "";
        public static string KT18 = "";
        public static string KT19 = "";
        public static string KT20 = "";
        public static string KT21 = "";
        public static string KT22 = "";
        public static string KT23 = "";
        public static string KT24 = "";
        public static string KT25 = "";
    }
```

- thực thi regex

```c#
 public static bool Regex_IsMatch(string Rexge, string str)
        {
            return Regex.IsMatch(str, Rexge);
        }
```
