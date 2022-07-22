## Cấu hình Https cho app reactjs

STEP: 1 Chạy Cmd với quyền administrator

STEP: 2 Cài đặt mkcert globally => npm install -g mkcert 

![image](https://user-images.githubusercontent.com/63473793/167229879-a57a73ea-6c86-4768-9ff9-b7896965d98a.png)

STEP: 3 Chạy 2 lệnh mkcert create-ca và mkcert create-cert

![image](https://user-images.githubusercontent.com/63473793/167229956-744182c9-c39f-4e24-99f8-eed9369bb27b.png)

Chúng ta sẽ có những file sau 

![image](https://user-images.githubusercontent.com/63473793/167230015-573065cd-3416-42bf-aa64-bb90412dd024.png)

STEP: 4 Double click vào file ca.cert

![image](https://user-images.githubusercontent.com/63473793/167230056-220d9781-b10b-4afe-9fb8-d66a0aaf7040.png)

STEP: 5 Click install certificate

![image](https://user-images.githubusercontent.com/63473793/167230063-78df399b-e580-4924-81c7-06b08d5d9092.png)

STEP: 6 Làm theo hình ảnh

![image](https://user-images.githubusercontent.com/63473793/167230142-e3c439a9-cd83-4a7f-8bb0-632ad6bb4e9b.png)

![image](https://user-images.githubusercontent.com/63473793/167230159-535d1898-e4c2-4e34-a80a-4c585df9d898.png)

![image](https://user-images.githubusercontent.com/63473793/167230164-4c3d75f1-f50a-4eb8-9a8d-7a9fe347ba67.png)

Double click lại chúng ta có 

![image](https://user-images.githubusercontent.com/63473793/167230191-6a2ecb33-4571-479d-b129-438ddb0ac7a0.png)

STEP: 7 Chạy ứng dụng set HTTPS=true&&set SSL_CRT_FILE=C:/Windows/System32/cert.crt&&set SSL_KEY_FILE=C:/Windows/System32/cert.key&&set PORT=7000 && craco start
