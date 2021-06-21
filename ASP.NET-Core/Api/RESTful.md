# Định Nghĩa 
> API (Application Programming Interface) là một tập các quy tắc và cơ chế mà theo đó, một ứng dụng hay một thành phần sẽ tương tác với một ứng dụng hay thành phần khác. API có thể trả về dữ liệu mà bạn cần cho ứng dụng của mình ở những kiểu dữ liệu phổ biến như JSON hay XML.

> REST (REpresentational State Transfer) là một dạng chuyển đổi cấu trúc dữ liệu, một kiểu kiến trúc để viết API. Nó sử dụng phương thức HTTP đơn giản để tạo cho giao tiếp giữa các máy. Vì vậy, thay vì sử dụng một URL cho việc xử lý một số thông tin người dùng, REST gửi một yêu cầu HTTP như GET, POST, DELETE, vv đến một URL để xử lý dữ liệu.

> RESTful API là một tiêu chuẩn dùng trong việc thiết kế các API cho các ứng dụng web để quản lý các resource. RESTful là một trong những kiểu thiết kế API được sử dụng phổ biến ngày nay để cho các ứng dụng (web, mobile…) khác nhau giao tiếp với nhau.

> Chức năng quan trọng nhất của REST là quy định cách sử dụng các HTTP method (như GET, POST, PUT, DELETE…)  và cách định dạng các URL cho ứng dụng web để quản các resource. RESTful không quy định logic code ứng dụng  và không giới hạn bởi ngôn ngữ lập trình ứng dụng, bất kỳ ngôn ngữ hoặc framework nào cũng có thể sử dụng để thiết kế một RESTful API.

## Client Yêu cầu Dữ liệu HTTP Request
> tổng cộng có 9 loại thường gặp cx có thể là 15 tùy hứng 

| HTTP method | Ý Nghĩa                                                           |
|-------------|-------------------------------------------------------------------|
| GET         | được sử dụng để lấy thông tin từ server theo URI đã cung cấp.     |
| HEAD        | giống với GET nhưng response trả về không có body, chỉ có header. |
| POST        | gửi thông tin tới sever thông qua các biểu mẫu http.              |
| PUT         | ghi đè tất cả thông tin của đối tượng với những gì được gửi lên.  |
| PATCH       | ghi đè các thông tin được thay đổi của đối tượng.                 |
| DELETE      | xóa tài nguyên trên server.                                       |
| CONNECT     | thiết lập một kết nối tới server theo URI.                        |
| OPTIONS     | mô tả các tùy chọn giao tiếp cho resource.                        |
| TRACE       | thực hiện một bài test loop – back theo đường dẫn đến resource.   |
> thật ra là kiểu nào cũng được không ai yêu cầu là get là bắt buộc lấy thông tin, hay post là gửi thông tin
## Server trả về trạng thái HTTP Response

| Trạng thái | Tên                        | Ý NGhĩa                                                                                                     |
|------------|----------------------------|-------------------------------------------------------------------------------------------------------------|
| 200        | OK                         | Trả về thành công cho những phương thức GET, PUT, PATCH hoặc DELETE.                                        |
| 201        | Created                    | Trả về khi một Resouce vừa được tạo thành công.                                                             |
| 204        | No Content                 | Trả về khi Resource xoá thành công.                                                                         |
| 304        | Not Modified               | Client có thể sử dụng dữ liệu cache.                                                                        |
| 400        | Bad Request                | Request không hợp lệ                                                                                        |
| 401        | Unauthorized               | Request cần có auth.                                                                                        |
| 403        | Forbidde                   | bị từ chối không cho phép.                                                                                  |
| 404        | Not Found                  | Không tìm thấy resource từ URI                                                                              |
| 405        | Method Not Allowed         | Phương thức không cho phép với user hiện tại.                                                               |
| 410        | Gone                       | Resource không còn tồn tại, Version cũ đã không còn hỗ trợ.                                                 |
| 415        | Unsupported Media Type     | Không hỗ trợ kiểu Resource này.                                                                             |
| 422        | Unprocessable Entit        | Dữ liệu không được xác thực                                                                                 |
| 429        | Too Many Requests          | Request bị từ chối do bị giới hạn                                                                           |
| 500        | Internal Server Error      | Một thông báo chung, được đưa ra khi máy chủ gặp phải một trường hợp bất ngờ, message cụ thể không phù hợp. |
| 501        | Not Implemented            | Máy chủ không công nhận các phương thức yêu cầu hoặc không có khả năng xử lý nó.                            |
| 502        | Bad Gateway                | Máy chủ đã hoạt động như một gateway hoặc proxy và nhận được một phản hồi không hợp lệ từ máy chủ nguồn.    |
| 503        | Service Unavailable        | Máy chủ hiện tại không có sẵn (hiện đang quá tải hoặc bị down để bảo trì). Đây chỉ là trạng thái tạm thời.  |
| 504        | Gateway Timeout            | Máy chủ đã hoạt động như một gateway hoặc proxy và không nhận được một phản hồi từ máy chủ nguồn.           |
| 505        | HTTP Version Not Supported | Máy chủ không hỗ trợ phiên bản “giao thức HTTP”.                                                            |

> về căn bản thì các XX sau thì cx không cần định nghĩa quá sâu nhưng cần có sự thống nhất. ví dụ như một ông BE nói với 1 ông FE là RESTful đi thì ông FE kia nhìn vào tên và trạng thái là biết mình cần làm gì
## HTTP Status Codes 
> trong đó Một số loại thông dụng mà server trả về cho client như sau:
1. 1xx: information Message
```Console
Các status code này chỉ có tính chất tạm thời, client có thể không quan tâm.
```
2. 2xx Successful
```Console
Khi đã xử lý thành công request của client, server trả về status dạng này:

 200 OK: request thành công.
 202 Accepted: request đã được nhận, nhưng không có kết quả nào trả về, thông báo cho client tiếp tục chờ đợi.
 204 No Content: request đã được xử lý nhưng không có thành phần nào được trả về.
 205 Reset: giống như 204 nhưng mã này còn yêu câu client reset lại document view.
 206 Partial Content: server chỉ gửi về một phần dữ liệu, phụ thuộc vào giá trị range header của client đã gửi.

```

3. 3xx Redirection
```Console
Server thông báo cho client phải thực hiện thêm thao tác để hoàn tất request:

301 Moved Permanently: tài nguyên đã được chuyển hoàn toàn tới địa chỉ Location trong HTTP response.
303 See other: tài nguyên đã được chuyển tạm thời tới địa chỉ Location trong HTTP response.
304 Not Modified: tài nguyên không thay đổi từ lần cuối client request, nên client có thể sử dụng đã lưu trong cache.
```

4. 4xx Client error
```Console
Lỗi của client:

400 Bad Request: request không đúng dạng, cú pháp.
401 Unauthorized: client chưa xác thực.
403 Forbidden: client không có quyền truy cập.
404 Not Found: không tìm thấy tài nguyên.
405 Method Not Allowed: phương thức không được server hỗ trợ.
```

5. 5xx Server Error
```Console
Lỗi của server:

500 Internal Server Error: có lỗi trong quá trình xử lý của server.
501 Not Implemented: server không hỗ trợ chức năng client yêu cầu.
503 Service Unavailable: Server bị quá tải, hoặc bị lỗi xử lý.
```
> Thật ra bài này không hề đặt trọng tâm là RESTful nhưng như vậy cx đã quá đủ dùng và phù hợp với trạng thái public của blog