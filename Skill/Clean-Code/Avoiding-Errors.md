# Catching and Avoiding Errors (Bắt và phòng tránh lỗi)

## Các quy tắc bắt buộc

- Khi gặp lỗi, hàm không trả về mã lỗi, phải ném ra Exception
- Khi ném ra một Exception, nên cung cấp đầy đủ thông tin về lỗi
- Bọc các Exception của một API bên thứ ba vào làm một Exception tự định nghĩa
- Không return giá trị null
- Không truyền giá trị null vào tham số hàm

## Phân loại Nội dung Diễn giải

* Bắt và phòng tránh lỗi
Khi gặp lỗi, hàm không trả về mã lỗi, phải ném ra Exception
Khi gặp lỗi, hàm không nên return ra mã lỗi mà nên ném ra một ngoại lệ. Bởi vì nếu trả về mã lỗi, nơi gọi hàm sẽ phải kểm tra kết quả mã lỗi là gì, rồi mới quyết định được là thực hiện được hành
động gì. Do đó sẽ làm cho chương trình rối rắm, phức tạp. Thay vào  đó, nên sử dụng cơ chế bắt và ném lỗi sẽ làm cho chương trình sạch
hơn.
* Khi ném ra một Exception, nên cung cấp đầy đủ thông tin về lỗi
Khi ném ra một Exception, nên cung cấp đầy đủ thông tin về lỗi bao gồm: nội dung lỗi (có thể là mã lỗi, message), stack trace.
 Điều này giúp có đầy đủ thông tin để log lỗi, dò vết lỗi.
* Bọc các Exception của một API bên thứ ba vào làm một Exception tự định nghĩa
Khi sử dụng một API của bên thứ 3, nên viết một lớp bọc cho API đó, đặc biệt là bọc hàm và kiểu exception,
 để bảo đảm giảm thiểu sự phụ thuộc vào API đó.
Ví dụ một API bên thứ 3 là AcmePort có định nghĩa 3 loại Exception là: DeviceResponseException, AtmUnlockedException, GmxException.
Ta nên định nghĩa một loại Exception là PortDeviceException:
- Viết hàm gọi sang hàm của AcmePort
- Nếu AcmePort ném ra một trong 3 loại Exception trên, thì tạo ra một PortDeviceException mới và có mã lỗi thể hiện exception mới tạo ra là Device, AtmUnLocked hay Gmx
* Không return null
Việc một hàm return null sẽ khiến cho nơi gọi hàm đó phải vất vả xử lý 2 trường hợp: return null hoặc return khác null.
Nếu bạn đang return null trong một phương thức, bạn nên refactor code theo một trong 2 cách sau:
- Ném ra Exception báo là null
- Return giá trị mặc định của object đó
* Không truyền null vào hàm
Nếu truyền null vào hàm, thì hàm đó lúc nào cũng phải kiểm tra ít nhất hai trường hợp: tham số null hay khác null. Do đó logic của
hàm trở nên phức tạp, hàm dài, bẩn.
Khi xử lý một tham số đầu vào của hàm, và hàm đó là hàm nội bộ (không phải là api đưa ra bên ngoài),
 thì ta có thể giả thiết là tham số đó khác null và xử lý, không cần bước kiểm tra null.
Ở những nơi gọi hàm phía trên, phải bảo đảm là không được phép truyền null vào hàm đó.

## Phân loại Nội dung Chi tiết
* Bắt lỗi Nên sử dụng unchecked exception
[Đặc biệt cho Java]:
Nên ném ra unchecked exception (không bắt buộc phải try... catch hay throws tại thời điểm biên dịch) thay vì ném ra checked exception (bắt
buộc try... catch hoặc throws).