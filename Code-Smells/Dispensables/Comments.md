# Comments
- Không sử dụng comment để giải thích đoạn code khi có thể tách đoạn code đó ra thành một hàm với tên mô tả đúng mục đích
- Trước khi viết một comment để giải thích một vấn đề gì đó, bạn phải cân nhắc thật kỹ xem: liệu có thể đặt tên hàm, tên biến mô tả chi tiết vấn đề đó không (không ngại tên biến, tên hàm dài). Nếu có thể, hãy đặt chúng và xóa comment đi.
- Không để tồn tại những comment dư thừa, vô nghĩa
- Không comment những thông tin dư thừa, vô nghĩa.
- Không sử dụng comment để theo dõi sự thay đổi code
- Tuyệt đối cấm dùng comment chỉ để ghi thời gian thay đổi code, người thay đổi code (đã được ứng dụng quản lý code thực hiện).
- Không bao giờ đưa tạm một đoạn code thành đoạn comment với mục đích trong tương lai sẽ mở ra sử dụng (chưa biết khi nào)
- Không nên comment tạm các đoạn code lại rồi commit lên. Phải xóa các đoạn code đó đi. Sau này nếu muốn tìm lại có thể lên xem history của trình quản lý code. Bởi vì sau một thời gian, chính lập trình viên comment out đoạn code đó cũng có thể quên chính mình là người tạo ra. Vì vậy đoạn code trong comment đó sẽ ở đó mãi mãi, và không ai biết là có nên xóa nó đi hay không.
- Không được dùng những comment chỉ để đánh dấu nơi bắt đầu, kết thúc các đoạn code
Không được dùng những comment chỉ để đánh dấu nơi bắt đầu, kết thúc các đoạn code. Trong trường hợp bạn cần comment để đánh dấu như vậy, chứng tỏ hàm của bạn rất dài. Bạn hãy refactor code bằng cách cắt toàn bộ đoạn code (từ chỗ đánh dấu bắt đầu tới chỗ đánh dấu kết thúc) ra thành một hàm khác.
- Không viết docs cho các hàm/class không public ra ngoài Chỉ được phép viết docs cho những hàm/class public ra ngoài. Bởi vì hàm/class dùng nội bộ trong project: lập trình viên có thể đọc tên hàm, tên biến, logic của hàm để hiểu, không cần thiết phải đọc docs. Trong khi đó nỗ lực duy trì docs là rất lớn. 