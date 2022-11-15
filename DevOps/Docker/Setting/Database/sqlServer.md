docker run -e "ACCEPT_EULA=Y" --name sqlserver-B6c -e "SA_PASSWORD=Sa123456" -v D:/mssql/:/var/opt/mssql/ -p 1434:1433 -d mcr.microsoft.com/mssql/server:2022-latest


host : 127.0.0.1,1434
userName : SA
Password : Sa123456
