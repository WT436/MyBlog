* Cài đặt nuget
```c#
	Microsoft.EntityFrameworkCore.SqlServer
	Microsoft.EntityFrameworkCore
	Microsoft.EntityFrameworkCore.Tool
```
* Tools => nuget package => Package Manager Console => Nhập Đoạn Code 
```c#
Scaffold-DbContext "Server=SerVerName;Database=DataBaseName;Trusted_Connection=True; User ID=Account;Password=Pass"Microsoft.EntityFrameworkCore.SqlServer -OutputDir Models/NewFolder
```
* Chúng Ta sẽ được một file class chuyển hóa từ db sql server ra như sau 
![image](https://user-images.githubusercontent.com/63473793/89106177-e0f7d800-d451-11ea-8745-a8b8f5afef50.png)
* nếu chỉ Muốn Đơn giản để connect đk dataBase thì Chỉ Cần NTN là đủ dùng 
nếu muốn thay đổi thì x2 click vô project 
delete 
```c#
<IncludeAssets>runtime; build; native; contentfiles; analyzers; buildtransitive</IncludeAssets>
```