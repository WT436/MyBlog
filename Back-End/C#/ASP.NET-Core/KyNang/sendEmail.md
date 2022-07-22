```c#
  public static class SeendMail
    {
        public static bool seend(string emailTo, string TieuDe, string noidung)
        {
            try
            {
                MailMessage mail = new MailMessage();
                SmtpClient SmtpServer = new SmtpClient("smtp.gmail.com");

                mail.From = new MailAddress("hainam1507x@gmail.com");
                mail.To.Add(emailTo);
                mail.Subject = TieuDe;
                mail.Body = noidung;

                SmtpServer.Port = 587;
                SmtpServer.Credentials = new System.Net.NetworkCredential("hainam1507x", "hainam9xtb");
                SmtpServer.EnableSsl = true;

                SmtpServer.Send(mail);

                return true;
            }
            catch (Exception)
            {
                return false;
            }

        }
    }
```
