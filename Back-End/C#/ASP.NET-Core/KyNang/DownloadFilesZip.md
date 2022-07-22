# Tải file từ server xuống cho client

- cài đặt thư viện SharpZipLib.NETStandard
  ![image](https://user-images.githubusercontent.com/63473793/89181316-a57a1c80-d5bd-11ea-9e6c-f411cb3e583d.png)
- Code C#

```c#
public FileResult DownloadingMultipleFiles()
        {
            var webRoot = _host.WebRootPath;
            var nameFile = "TesstZipFile.zip";
            var outputFile = webRoot + "/IMG/" + nameFile;

            using (ZipOutputStream zip = new ZipOutputStream(System.IO.File.Create(outputFile)))
            {
                zip.SetLevel(9);

                byte[] bu = new byte[4096];

                var iList = new List<string>();

                // có thể Kết nối csdl để lấy tên file cần zip
                iList.Add(webRoot + "/IMG/" + "download (1).jpg");
                iList.Add(webRoot + "/IMG/" + "download (1).png");
                iList.Add(webRoot + "/IMG/" + "download (2).jpg");
                iList.Add(webRoot + "/IMG/" + "download (2).png");
                iList.Add(webRoot + "/IMG/" + "[.net v11]Tran-Hai-Nam.pdf");

                for (int i = 0; i < iList.Count; i++)
                {
                    ZipEntry en = new ZipEntry(Path.GetFileName(iList[i]));
                    en.DateTime = DateTime.Now;
                    en.IsUnicodeText = true;
                    zip.PutNextEntry(en);

                    using (FileStream of = System.IO.File.OpenRead(iList[i]))
                    {
                        int sb;
                        do
                        {
                            sb = of.Read(bu, 0, bu.Length);
                            zip.Write(bu, 0, sb);
                        } while (sb > 0);
                    }
                }
                zip.Finish();
                zip.Flush();
                zip.Close();
            }

            byte[] fr = System.IO.File.ReadAllBytes(outputFile);

            if (System.IO.File.Exists(outputFile))
            {
                System.IO.File.Delete(outputFile);
            }

            if (fr == null || !fr.Any())
            {
                throw new Exception(string.Format("Có Biến Rồi Đại Vương"));
            }

            return File(fr, "aplication/zip", nameFile);
        }
```

![image](https://user-images.githubusercontent.com/63473793/89181357-bdea3700-d5bd-11ea-8ac1-233788f139b3.png)

```html
<a href="Home/DownloadingMultipleFiles" target="_blank">Tai xuong</a>
```

![image](https://user-images.githubusercontent.com/63473793/89181673-66989680-d5be-11ea-8279-63bba3462640.png)
