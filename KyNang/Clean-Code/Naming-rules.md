# Naming rules (Đặt tên biến/hàm/lớp)
1. Mục lục
- Đặt tên mô tả được mục đích sử dụng
- Tránh đặt tên dễ gây hiểu nhầm mục đích sử dụng
- Các tên khác nhau phải dễ phân biệt ý nghĩa, mục đích sử dụng khác nhau
- Không mã hóa kiểu, tiền tố, hậu tố vào tên
- Tên lớp, đối tượng phải là danh từ hoặc cụm danh từ
- Tên phương thức phải là động từ hoặc cụm động từ
- Không chọn những tên mang nghĩa đùa cợt, thiếu nghiêm túc
- Đối với mỗi một khái niệm chỉ sử dụng một tên duy nhất để đảm bảo sự thống nhất
- Không sử dụng một thuật ngữ cho hai mục đích/ý nghĩa sử dụng khác nhau
- Sử dụng tên là các giải pháp nổi tiếng trong việc giải quyết vấn đề ở lĩnh vực đó
- Sử dụng tên là các vấn đề nổi tiếng thường gặp ở lĩnh vực đó

2. Phân loại Nội dung Diễn giải

* Đặt tên mô tả được mục đích sử dụng
Chọn tên biến/hàm/class mô tả được chính xác ý nghĩa/mục đích sử dụng của nó, ngắn gọn, dễ hiểu.
- Nếu đặt tên biến mà cần comment bên cạnh để giải thích ý nghĩa của biến, thì có nghĩa tên biến đó chưa đúng
- Tương tự đối với tên hàm/lớp
* Tránh đặt tên dễ gây hiểu nhầm mục đích sử dụng
Ví dụ vì viết tắt nên người khác đọc sẽ hiểu thành ý nghĩa khác:
Biến tên hp có thể hiểu là tên hệ điều hành HP, hoặc là từ viết tắt của
Home Page.
* Các tên khác nhau phải dễ phân biệt ý nghĩa, mục đích sử dụng khác nhau
Tránh đặt tên hai hoặc nhiều biến có ý nghĩa gần giống nhau sẽ rất khó phân biệt.
Ví dụ không thể phân biệt được nameString và name khác nhau.
Ví dụ productInfo, product cũng không phân biệt được.
* Không mã hóa kiểu, tiền tố, hậu tố vào tên
Không thêm phần mã hóa kiểu, prefix... vào tên biến như phong cách lập trình C cũ.
Ví dụ vi phạm:
 phoneString
 bReadLine
 m_description
* Tên lớp, đối tượng phải là danh từ hoặc cụm danh từ
Tên class, tên biến phải là danh từ hoặc cụm danh từ.
Ví dụ hợp lệ: Customer, WikiPage, AddressParser
Ví dụ vi phạm: NotifyDAO
* Tên phương thức phải là động từ hoặc cụm động từ
Tên phương thức (hàm) phải là động từ/cụm động từ.
Ví dụ hợp lệ: deletePage(), save()
Ví dụ vi phạm: deletingPage(), saving()
* Không chọn những tên mang nghĩa đùa cợt, thiếu nghiêm túc
Không được phép đặt tên biến mang nghĩa đùa cợt, nghĩa ẩn dụ, không nghiêm túc.
Ví dụ: không đặt tên hàm là whack() với ý nghĩa là kill()
* Đối với mỗi một khái niệm chỉ sử dụng một tên duy nhất để đảm bảo sự thống nhất
Đối với mỗi khái niệm chỉ sử dụng một tên duy nhất để đảm bảo sự thống nhất. Ví dụ: không được phép sử dụng hàm với các tên khác
nhau "fetch", "retrieve", "get" với cùng một ý nghĩa là lấy dữ liệu.
* Không sử dụng một thuật ngữ cho hai mục đích/ý nghĩa khác nhau
Không sử dụng một tên cho hai mục đích/ý nghĩa khác nhau.
Ví dụ, không được phép đặt tên một hàm là add() để thêm mới data, trong khi đặt tên một hàm khác là add() để chèn một bản ghi đã có sẵn vào danh sách.
Hàm add() thứ hai nên được đổi tên thành insert().
* Sử dụng tên là các giải pháp nổi tiếng trong việc giải quyết vấn đề ở lĩnh vực đó
Được phép đặt tên với tiền tố/hậu tố là các solution domain.
Ví dụ, cho phép đặt tên class là AccountVisitor vì class đó sử dụng VISITOR design pattern.
* Sử dụng tên là các vấn đề nổi tiếng thường gặp ở lĩnh vực đó
Được phép đặt tên với tiền tố/hậu tố là các tên vấn đề (nổi tiếng). Như vậy khi người mới vào sẽ có thể biết cách google hoặc hỏi chuyên gia giải quyết vấn đề ở lĩnh vực đó.

3. Phân loại Nội dung Chi tiết

* Đặt tên biến/hàm/lớp
Phải đặt tên sao cho có thể đọc lên thành lời được
Phải đặt tên sao cho có thể đọc lên được. Khi đó các developer mới có thể nói chuyện với nhau được.
Ví dụ vi phạm:
Đặt tên như "ddmmYYYY" cho một biến sẽ rất khó đọc. Khi hai lập trình viên giao tiếp với nhau, và cần bàn luận về biến đó, phải đọc thành “di
di mờ mờ bốn chữ y”. Việc này sẽ làm cản trở việc giao tiếp giữa các lập trình viên.
Ví dụ hợp lệ:
Thay vì đặt là “ddmmYYYY” để chỉ giá trị là ngày được định dạng như vậy, có thể đặt tên biến là “formattedDate”
* Sử dụng các tên dễ tìm kiếm trong thư mục dự án
Phải đặt tên sao cho khi muốn xác định vị trí của tên đó trong toàn bộ project, ta có thể dễ dàng tìm kiếm.
Nếu đặt tên biến quá ngắn như "d", ta sẽ tìm ra chục hàng ngàn vị trí có từ "d", do đó sẽ không định vị được đâu là đúng biến "d" cần tìm.
* Nên sử dụng các tên thông dụng 
Khi cần miêu tả một thuật ngữ, nên chọn tên phổ biến mà nhiều người biết. 
Tránh việc đặt tên "lạ" dẫn tới người đọc phải suy diễn ra là tên đó giống với tên phổ biến kia.
Ví dụ: không đặt tên biến lặp là enumerators trong khi nhiều người biết rằng biến lặp phổ biến là iterators.
* Phạm vi của biến được sử dụng càng xa, thì được phép đặt tên biến càng dài
Phạm vi của biến được sử dụng càng xa, thì được phép đặt tên biến càng dài.
Thứ tự phạm vi theo tứ tự giảm dần: fields -> parameters -> locals -> loop variables
* Đặt tên biến phải dựa vào ngữ cảnh phù hợp
Để hiểu được một biến, ngoài việc đặt tên mô tả chính xác biến, thì cần đặt biến trong một ngữ cảnh phù hợp: 
ví dụ đặt trong class, function, namespace.
* Không thêm thông tin dư thừa vào tên biến
Không nên đặt tên biến dài quá, chứa nhiều thông tin không cần thiết.
Ví dụ vi phạm:
- Đặt tên biến là “customerInfo”
- Trong khi ai cũng hiểu “customer” là biến nói về customer
Ví dụ hợp lệ:
- Chỉ cần đặt tên biến là “customer” là đủ