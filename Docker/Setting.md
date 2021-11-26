Khi cài đặt thông thường có thể sẽ gặp cái modal ntn. Có thể bỏ qua nhưng nhìn nó rất ngứa mắt nên tôi sẽ fix nó luôn.
![image](https://user-images.githubusercontent.com/63473793/143525955-f054172e-9bab-4a9f-a82b-b889e3f9b75c.png)

Tại sao lại có cái model này trên win : 
- docker chỉ là công nghệ ảo hóa, nó tận dụng lại phần lõi của hdh vật lý khác với VM là VM nó sẽ cài thêm hdh vậy nên docker rất nhẹ, nhưng nó phải mất đi sự tự do. Win nó cũng có hỗ trợ cái này đó là hyper-V ở Control Panel\Programs\Programs and Features\turn windows features on or off. nhưng khi cài docker nó sẽ hỏi và yêu cầu kích hoạt.
- Bản thân thằng docker này nó lại hỗ trợ trên linux full packages nên cần lựa chọn cài máy ảo linux trên đó cho docker chạy là quá hợp lý luôn.

Nguồn tham khảo : [Tại đây](https://superuser.com/questions/1584710/docker-wsl-2-installation-is-incomplete)

Chúng ta có 2 cách :
 * Using WSL 2 based engine
 * Without using WSL 2 based engine

Tôi sẽ chạy cách 1 : làm tương tự như hướng dẫn là được ([Tại đây](https://docs.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)) :)
