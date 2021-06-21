# Shotgun Surgery

## Dấu Hiệu Nhận Biết
- Thực hiện bất kỳ sửa đổi nào đòi hỏi bạn phải thực hiện nhiều thay đổi nhỏ đối với nhiều lớp khác nhau.
![image](https://user-images.githubusercontent.com/63473793/121808652-c0a8c480-cc83-11eb-9def-8d9ada505a3e.png)
- Một trách nhiệm duy nhất đã được phân chia cho một số lượng lớn các Class. Điều này có thể xảy ra sau khi áp dụng quá mức Copy-Paste.

## Giải pháp
- Sử dụng Method Move và Move Field để di chuyển các hành vi của Class hiện có vào một Class duy nhất.
- Nếu không có Class nào thích hợp cho việc này, hãy tạo một Class mới.
- Nếu việc Move Code đến cùng một Class khiến các Class ban đầu gần như trống, hãy cố gắng loại bỏ các Class hiện đang dư thừa này thông qua Class nội tuyến.
![image](https://user-images.githubusercontent.com/63473793/121808739-2432f200-cc84-11eb-98d5-43dc3f0b8168.png)
- Tổ chức tốt hơn. 
- Ít trùng lặp mã.
- Bảo trì dễ dàng hơn.
- ![image](https://user-images.githubusercontent.com/63473793/121808760-3dd43980-cc84-11eb-82a1-60c33573d924.png)