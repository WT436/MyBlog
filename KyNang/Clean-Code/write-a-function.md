# How to write a function (Cách viết hàm)
## Các quy tắc bắt buộc
- Một hàm phải nhỏ, số lượng dòng code không quá 50 dòng
- Mỗi hàm chỉ làm một việc
- Tên hàm phải mô tả được các hành động mà hàm đó thực thi, tránh hiệu ứng lề
- Bố cục giảm dần
- Không được sử dụng output argument
- Không lặp code
- Số lượng tham số của hàm không được lớn hơn 3
- Hạn chế tối đa việc sử dụng tham số có kiểu là Boolean
- Luật: Command Query Separation
## Phân loại Nội dung Diễn giải
* Cách viết hàm 
-Một hàm phải nhỏ, số lượng dòng code không quá 50 dòng
-Nếu một đoạn code trong hàm có thể tách ra thành một hàm con khác, chứng tỏ hàm hiện thời quá dài. Bắt buộc phải refactor code.
Một hàm nên đủ nhỏ (không tràn quá màn hình), giúp người đọc có thể hiểu mà không cần comment hay viết tài liệu.
* Mỗi hàm chỉ làm một việc Một hàm chỉ làm một việc duy nhất, không được gộp quá nhiều logic xử lý vào trong cùng một hàm.
* Tên hàm phải mô tả được các hành động mà hàm đó thực thi, tránh hiệu ứng lề
Khi đặt tên hàm là gì thì phải bảo đảm hàm đó làm đúng như mô tả, không được phép làm ít hơn hoặc nhiều hơn. Đặc biệt nghiêm cấm 
việc làm thay đổi giá trị các biến toàn cục, tài nguyên hệ thống,... trong khi tên hàm không hề đề cập tới việc này.
- Ví dụ hợp lệ: hàm updateProject() thực thi một hành động duy
nhất là cập nhật thông tin Project vào trong database
- Ví dụ vi phạm: hàm updateProject () làm các việc:
    + Cảnh báo nếu nỗ lực dự kiến của Project nhỏ hơn nỗ lực thực tế
    + Cập nhật thông tin Project vào trong database
    + Cập nhật thông tin các mốc Milestones của Project vào trong database
    + Sau khi cập nhật thành công thì khởi tạo Session
* Bố cục giảm dần Hàm gọi sẽ đứng trước hàm được gọi, và đứng gần nhất có thể.
* Không được sử dụng output argument Không được phép sử dụng output argument. Nếu cần trả về kết quả thì sử dụng "return".
* Không lặp code
-Nghiêm cấm việc lặp đi lặp lại các đoạn code. Nếu có các đoạn code lặp lại (kể cả ở các hàm khác nhau, các class khác nhau), cần refactor chúng ra thành một hàm.

## Phân loại Nội dung Chi tiết

Số lượng tham số của hàm không được lớn hơn 3
    - Hàm không có tham số: rất tốt
    - Hàm có một tham số: tốt
    - Hàm có 2 tham số: được. Nhưng nên cân nhắc việc chuyển đổi hàm về dạng 1 tham số nếu có thể
    - Hàm có 3 tham số: chấp nhận được. Tuy nhiên không khuyến khích.
Vì khi hàm có 3 tham số, có nghĩa là số test case viết test cho hàm đó là rất nhiều.
    - Hàm có 4 tham số trở lên: rất tồi
Do đó giải pháp nâng cao chất lượng hàm là:
    - Nếu hàm có 2 tới 3 tham số, luôn luôn cố gắng xem có thể biến đổi về dạng hàm có 0 hoặc 1 tham số không. 
Trường hợp thực sự cần thiết mới cho phép 2 tới 3 tham số.
    - Nếu hàm có nhiều hơn 3 tham số, thì các tham số nên được nhóm vào trong một object/data structure.

* Hạn chế tối đa việc sử dụng tham số có kiểu là Boolean
Hạn chế tối đa việc sử dụng tham số có kiểu là Boolean bởi vì khi gọi hàm f(true), f(false),
người đọc sẽ rất khó hiểu ý nghĩa. Cố gắng refactor thành 2 hàm khác nhau, một hàm cho f(true) và một hàm cho f(false).
Ví dụ vi phạm:
public void render(boolean isSingle){
 if(isSingle){
 ... thực hiện render cho một unit test ...
 } else {
 ... thực hiện render cho một nhóm các unit
test (suite) ...
 }
}
Ví dụ hợp lệ: tách hàm render ra thành 2 hàm
public void renderForSingle()
public void renderForSuite()
* Command Query Separation
Một hàm có thể dùng để thực thi một hành động gì đó, hoặc là trả ra một kết quả gì đó, nhưng không được phép làm cả 2 việc.
Ví dụ vi phạm:
public boolean set(String attribute, String value)
Hàm này sẽ lưu giá trị value vào cột attribute trong một bảng ở database. 
Tuy nhiên sau đó, hàm lại return true hoặc false để biểu thị rằng attribute đó có đang tồn tại giá trị hay không. 
Hàm này làm 2 việc một lúc là không phù hợp.
Ví dụ hợp lệ: tách hàm phía trên thành 2 hàm
public void set(String attribute, String value)
public boolean isExisting(String attribute, String value)
* Cấu tạo lớp/cấu trúc Data/Object Anti-Symmetry 
Cân nhắc khi thiết kế hệ thống:
    - Khi cần thường xuyên thêm mới hàm thì chọn kiểu dữ liệu là Procedure
    - Khi cần thường xuyên thêm mới kiểu dữ liệu, không thay đổi hàm thì chọn kiểu Object
* Không đặt các phương thức logic vào data structure
Nếu kiểu dữ liệu là data structure (ví dụ DTO, Bean, Active Record) thì không nên thêm các hàm thực hiện business logic vào.
* Nguyên tắc tri thức tối thiểu
Nguyên tắc tri thức tối thiểu: không nên tham chiếu một đối tượng sâu hơn một lớp. 
Nguyên tắc này được gọi nôm na là "không được phép nói chuyện với người lạ).
Ví dụ ta cần viết code trong hàm f, thuộc class C, thì dòng code đó phải
tuân theo rule sau:
- Được phép gọi hàm của:
    + Class C
    + Object là tham số của hàm f
    + Object là biến instance của class C
    + Object là biến cục bộ được tạo trong hàm f
- Không được phép gọi hàm của object là tham chiếu được trả về từ một
lời gọi hàm.
Ví dụ vi phạm: objectA.getObjectB().doSomething();
Ví dụ hợp lệ: viết một phương thức doSomeThingInB() trong object A:
doSomethingInB(){
 getObjectB.doSonething()
}
==> Sau đó thay vì gọi hàm doSomething() như ví dụ vi phạm, ta có thể gọi hàm mới: objectA.doSomethingInB()