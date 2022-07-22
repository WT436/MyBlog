# Action Results

1. IActionResult and ActionResult

   - IActionResult là một inyerface , định nghĩa một hợp đồng đại diện cho kết quả của một action .
   - ActionResult là một lớp cơ sở trừu tượng thực hiện IActionResult.
   - Các kết quả Hành động như ViewResult, PartialViewResult, JsonResult, v.v. bắt nguồn từ lớp cơ sở ActionResult.

2. ContentResult

- cái này sẽ trả về 1 đoạn string

  ```c#
  public class HomeController : Controller {
  public ContentResult Index()
  {
      ContentResult v = new ContentResult();
      v.Content = "Hello World";
      return v;
  }
  }
  ```

3. Return Type

   - The Index method above returns the ContentResult.
   - Tôi thích là sử dụng ActionResult làm Kiểu trả về như hình dưới đây.

   ```c#
   public ActionResult Index(int Nam)
   {
        if (Nam==0) {
            return NotFound();
        }
        else {
            return Content("NamString");
        }
   }
   ```

4. Action Result Sets

- Có nhiều Kết quả Hành động có sẵn trong không gian tên Microsoft.AspNetCore.Mvc. Chúng có thể được phân loại rộng rãi dựa trên cách sử dụng của chúng như sau.

- Producing the HTML
- Redirecting the Users
- Returning Files
- Content Results
- Returning Errors and HTTP Codes
- Security Related Results

5.  Producing the HTML

    - Có hai Action results, sử dụng mô hình để hiển thị Phản hồi HTML. ViewResult và PartialViewResult.

    1.  ViewResult

    - Phương thức View() tìm kiếm View trong thư mục Views / < Controller > để định vị tệp .cshtml và phân tích cú pháp nó bằng cách sử dụng công cụ chế độ xem Razor. Bạn cũng có thể đưa dữ liệu mô hình vào dạng xem. Phương thức View trả về ViewResult, kết quả này tạo ra HTML Response.

    ```c#
        public ActionResult Index()
        {
            var movie = new Movie() { Name = "Avatar" };
            return View(movie);
        }
    ```

    2.  PartialViewResult

    - trả về thành phần trang cho view chính

6.  Redirecting the Users

- Kết quả Chuyển hướng được sử dụng khi bạn muốn chuyển hướng đến một URL khác

  1. RedirectResult

  - RedirectResult sẽ chuyển hướng người dùng đến URL tương đối hoặc tuyệt đối được cung cấp

  ```c#
  Action Result	        Controller method	            Status Code
  RedirectResult	    Redirect	                    302 Found (Temporarily moved)
                        RedirectPermanent	            301 Moved Permanently
                        RedirectPermanentPreserveMethod	308 Permanent Redirect
                        RedirectPreserveMethod	        307 Temporary Redirect
  ```

  ```c#
    Redirect("/Product/Index");
    RedirectPermanent("/Product/Index");
    RedirectPermanentPreserveMethod("/Product/Index");
    RedirectPreserveMethod("/Product/Index");
  ```

  2. LocalRedirectResult

  - Kết quả hành động này tương tự như RedirectResult với một ngoại lệ. Chỉ các URL cục bộ mới được chấp nhận. Nếu bạn cung cấp bất kỳ URL bên ngoài nào, phương pháp này sẽ ném ra một lỗi không hợp lệ.

    ```c#
        Action Result           Controller method                    Status Code
        LocalRedirectResult     LocalRedirect                        302 Found (Temporarily moved)
                                LocalRedirectPermanent               301 Moved Permanently
                                LocalRedirectPermanentPreserveMethod 308 Permanent Redirect
                                LocalRedirectPreserveMethod          307 Temporary Redirect

        VD :
        LocalRedirect("/Product/Index");
        LocalRedirectPermanent("/Product/Index");
        LocalRedirectPermanentPreserveMethod("/Product/Index");
        LocalRedirectPreserveMethod("/Product/Index");
    ```

    3. RedirectToActionResult

    - action result này chuyển hướng khách hàng đến một action and controller cụ thể. Nó có action name, controller name, and route value.

    ```c#
    Action Result	        Controller method	                    Status Code
    RedirectToActionResult	RedirectToAction	                    302 Found (Temporarily moved)
                            RedirectToActionPermanent	            301 Moved Permanently
                            RedirectToActionPermanentPreserveMethod	308 Permanent Redirect
                            RedirectToActionPreserveMethod	        307 Temporary Redirect
    VD :
    RedirectToAction(actionName: "Index", controllerName: "Home");
    RedirectToAction(actionName: "Index");
    ```

    4. RedirectToRouteResult

    - action result này chuyển hướng khách hàng đến một route cụ thể. Nó lấy route name, route value and chuyển hướng chúng ta đến route đó với các giá trị tuyến được cung cấp.

    ```c#
    Action Result	            Controller method	                    Status Code
    RedirectToRouteResult	    RedirectToRoute	                        302 Found (tạm thời)
                                RedirectToRoutePermanent	            301 Moved Permanently
                                RedirectToRoutePermanentPreserveMethod	308 Permanent Redirect
                                RedirectToRoutePreserveMethod	        307 Temporary Redirect

    VD :
    return RedirectToRoute("default");
    var routeValue = new RouteValueDictionary(new { action = "Index", controller = "Home"});
    return RedirectToRoute(routeValue);
    ```

7.  Returning Files

- FileResult là Action Result sử dụng hành động Controller để cung cấp các tệp cho người dùng.

  1. FileResult

  - FileResult Đại diện cho một lớp cơ sở được sử dụng để gửi nội dung tệp nhị phân tới phản hồi. Nó là một lớp cơ sở trừu tượng, được thực hiện bởi FileContentResult, FileStreamResult, VirtualFileResult và PhysicalFileResult. Các lớp này đảm nhận công việc trả lại tệp cho máy khách.

  2. FileContentResult

  - FileContentResult đọc từ một mảng byte và trả về dưới dạng tệp

    ```c#
    return new FileStreamResult(fileStream, "application/pdf");
    ```

  3. FileStreamResult

  - Kết quả hành động này đọc nội dung của tệp từ một đường dẫn liên quan đến ứng dụng trên máy chủ và gửi nội dung đến máy khách dưới dạng tệp.
    ```c#
    return new PhysicalFileResult("c:/path/filename", "application/pdf");
    ```

  4. VirtualFileResult

  - This action result reads the contents of a file from a path relative to the application on the host and sends the contents to the client as a file.

  5. PhysicalFileResult

  - Kết quả hành động này đọc nội dung của tệp từ một vị trí thực và gửi nội dung đến máy khách dưới dạng tệp. Lưu ý rằng đường dẫn phải là đường dẫn tuyệt đối.

8.  Content Results
    1. JsonResult
    - Kết quả hành động này trả về dữ liệu có định dạng JSON. Nó tuần tự hóa đối tượng đã cho thành JSON và trả về máy khách.
    ```c#
    public JsonResult About()
    {
        return Json(object);
    }
    ```
    2. ContentResult
    - ContentResult ghi trực tiếp nội dung được chỉ định vào phản hồi dưới dạng dữ liệu chuỗi có định dạng văn bản thuần túy.
    ```c#
    public ContentResult About()
    {
    return Content("Hello World");
    }
    ```
    3. EmptyResult
    - EmptyResult như tên cho thấy không trả về bất cứ điều gì. Sử dụng điều này khi bạn muốn thực thi một số logic bộ điều khiển, nhưng không muốn trả về bất kỳ thứ gì
    ```c#
    return new EmptyResult();
    ```
9.  Returning Errors and HTTP Codes

- Kết quả Hành động trong phần này thường được sử dụng trong bộ điều khiển API Web. Các Kết quả này sẽ gửi lại Mã trạng thái HTTP cho Khách hàng. Một số người trong số họ cũng có thể gửi một đối tượng trong phản hồi.

  1. StatusCodeResult

  - Kết quả hành động StatusCodeResult gửi một mã trạng thái HTTP được chỉ định đến máy khách.

    ```c#
    return StatusCode(200);
    or
    return new StatusCodeResult(200);
    ```

  2. ObjectResult

  - Kết quả hành động này sẽ sử dụng thương lượng nội dung để gửi một đối tượng đến máy khách và đặt Mã trạng thái HTTP 200. Quá tải của phương thức StatusCode có thể lấy một đối tượng làm đối số thứ hai và trả về một ObjectResult.

  ```c#
    return StatusCode(200, new { message = "Hello" });
    //or
    return new ObjectResult(new { message = "Hello" });
  ```

  > Note that the StatusCode controller helper method can send any status code along with an object.

  3. OkResult

  - Kết quả hành động này sẽ gửi mã trạng thái HTTP 200 đến máy khách.
    ```c#
    return Ok(new {message="Hello"});
    or
    return new OkObjectResult(new { message = "Not found" });
    ```

  4. OkObjectResult

  - tương tự trên

  5. CreatedResult

  - CreatedResult được sử dụng khi Tài nguyên được tạo sau Yêu cầu Đăng. Thao tác này sẽ gửi mã trạng thái 201 cùng với đối tượng được tạo.

    ```c#
    return Created(new Uri("/Home/Index", UriKind.Relative), new {message="Hello World"});
    or
    return new CreatedResult(new Uri("/Home/Index", UriKind.Relative), new { message = "Hello World" });
    ```

  6. CreatedAtActionResult

  - Kết quả Hành động này tương tự như Hành động CreatedResult nhưng lấy tên Bộ điều khiển & Hành động thay vì Uri.
    ```c#
    return CreatedAtAction("Index", new {message="Hello World"});
    ```

  7. CreatedAtRouteResult

  - Kết quả hành động này nhận các giá trị định tuyến và tương tự như Kết quả được tạo ra và Kết quả tạo ra hành động.
    ```c#
    CreatedAtRoute("default", new { mesage = "Hello World" });
    ```

  8. BadRequestResult

  - Kết quả hành động này gửi mã trạng thái HTTP 400 đến máy khách. Sử dụng mã trạng thái phản hồi này để chỉ ra cú pháp hoặc yêu cầu không hợp lệ không thể hiểu được.
    ```c#
    return BadRequest()
    ```

  9. BadRequestObjectResult

  - ActionResult này tương tự như BadRequestResult. Sự khác biệt là bạn có thể gửi ModelStateDictionary (là một đối tượng chứa thông tin chi tiết về lỗi) cùng với mã trạng thái 400.
    ```c#
    var meomeomeo = new ModelStateDictionary();
    meomeomeo.AddModelError("message", "errors");
    return BadRequest(meomeomeo);
    ```

  10. NotFoundResult

  - Kết quả hành động này gửi mã trạng thái HTTP 404 đến máy khách.
    ```c#
    return NotFound();
    ```

  11. NotFoundObjectResult

  - Kết quả hành động này tương tự như NotFoundResult, nhưng trả về một đối tượng cùng với mã trạng thái 404. Quá tải thứ hai của phương thức trợ giúp bộ điều khiển NotFound lấy một đối tượng làm đối số và trả về NotFoundObjectResult.
    ```c#
    return NotFound( new { message = "Not found" });
    ```

  12. UnsupportedMediaTypeResult

  - Kết quả hành động này gửi mã trạng thái HTTP 415 đến máy khách. Sử dụng kết quả hành động này, khi yêu cầu ở định dạng không được máy chủ hỗ trợ.
  - return new UnsupportedMediaTypeResult();

  13. NoContentResult

  - Kết quả hành động này sẽ gửi mã trạng thái HTTP 204. Sử dụng NoContentResult khi yêu cầu được thực hiện, nhưng không có nội dung nào để gửi lại cho khách hàng
  - return NoContent();

10. Security Related Results

    1. SignInResult

    - SignInResult Đại diện cho kết quả của một thao tác đăng nhập. SignInManager.SignInAsync hoặc PasswordSignInAsync trả về SignInResult, có bốn thuộc tính Succeeded, IsLockedOut, IsNotAllowed

    2. SignOutResult

    - SignOutResult Đại diện cho kết quả của một hoạt động đăng xuất.

    3. ForbidResult

    - ForbidResult trả về mã trạng thái 403 (Forbidden) khi người dùng không được phép thực hiện thao tác được yêu cầu trên tài nguyên đã cho.
    - ForbidResult không có nghĩa là người dùng không được xác thực. Người dùng chưa được xác thực sẽ nhận được ChallengeResult hoặc UnauthorisedResult.

    4. ChallengeResult

    - Kết quả Thách thức được trả về khi xác thực người dùng không thành công. Kết quả này sẽ thông báo cho bất kỳ phần mềm trung gian xác thực nào để thực hiện phản hồi thích hợp, ví dụ: trả lại mã trạng thái 401 (Không được phép) hoặc 403 (Bị cấm) hoặc chuyển hướng người dùng đến trang đăng nhập cho các ứng dụng trình duyệt tương tác.

    5. UnauthorizedResult

    - UnauthorizedResult trả về mã trạng thái phản hồi HTTP “401 - Unauthorized”. Phương thức lớp cơ sở Controller Unauthorized trả về một thể hiện của UnauthorizedResult.
