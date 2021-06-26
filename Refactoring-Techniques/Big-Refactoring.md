# Big Refactoring


1. Tease Apart Inheritance

Chúng ta có hệ thống phân cấp kế thừa đang thực hiện hai công việc cùng một lúc. Tạo hai phân cấp và sử dụng ủy quyền để gọi một phân cấp từ bên kia.

2. Converty Procedural Design to Objects 

Chúng ta có code được viết theo kiểu procedural. Chuyển các bản ghi dữ liệu thành các object, chia nhỏ hành vi và chuyển hành vi sang các object.

3. Separate Domain from Presentation

Chúng ta có các nhóm GUI chứa logic miền. Tách logic miền thành các class miền riêng biệt.

4. Extract Hierarchy

Chúng ta có một class đang làm quá nhiều việc, ít nhất là một phần thông qua nhiều câu lệnh điều kiện. Tạo một hệ thống phân cấp các class trong đó mỗi class con đại diện cho một trường hợp đặc biệt.

Trước tiên là khái niệm. Còn cách thực hiện ra sao thì sẽ update trong thời gian tới.

 <br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>