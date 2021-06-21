# Parallel Inheritance Hierarchies

## Dấu Hiệu Nhận Biết
- Bất cứ khi nào bạn tạo một Class con cho một Class, bạn sẽ thấy mình cần phải tạo một Class con cho một Class khác.
- Tất cả đều ổn miễn là hệ thống phân cấp vẫn nhỏ. Nhưng với việc các Class mới được thêm vào, việc thay đổi ngày càng trở nên khó khăn hơn.
## Giải pháp
- Bạn có thể khử trùng lặp phân cấp lớp song song trong hai bước. 
- Đầu tiên, hãy làm cho các trường hợp của một hệ thống phân cấp này tham chiếu đến các trường hợp của một hệ thống phân cấp khác. 
- Sau đó, loại bỏ cấu trúc phân cấp trong Class được giới thiệu, bằng cách sử dụng Move Method and Move Field.
- Giảm sự trùng lặp Code. 
- Có thể cải thiện tổ chức của Code.