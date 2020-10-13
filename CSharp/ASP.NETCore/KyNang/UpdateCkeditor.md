Đầu tiên chúng ta tải file ckeditor full trên Link https://ckeditor.com/ckeditor-4/download/

+Trong file hrtml chúng ta add tag

```js
<script src="~/lib/jquery/dist/jquery.min.js"></script>
<script src="~/ckeditor/ckeditor.js"></script>

- Khung Nhập dữ liệu

<textarea id="editor"></textarea>

-nút bấm  chuyển dữ liệu

<a href="#" class="taiDuLieuLen">Tải Lên</a>
```

+Trong file js
-khởi tạo khung dữ liệu

```js
$(document).ready(function () {
  CKEDITOR.replace("editor", {
    height: 400,
    filebrowserUploadUrl: "/Admin/UpLoadCKEditorSingGer",
  });
});
```

--trên server để tải ảnh lên trên

```c#
public JsonResult UpLoadCKEditorSingGer(IFormFile upload)
        {
            var fileName = DateTime.Now.ToString("yyyyMMddHHmmss") + upload.FileName;
            var file = Path.Combine(Directory.GetCurrentDirectory(), "wwwroot/ImagePost", fileName);
            upload.CopyToAsync(new FileStream(file, FileMode.Create));
            return new JsonResult(new
            {
                uploaded = 1,
                url = "/ImagePost/" + fileName
            });
        }
```

/************************************************\*\*\*\*************************************************/

-chuyển dữ liệu lên server dạng string

```c#
$('.taiDuLieuLen').click(() => {
    var a = CKEDITOR.instances['editor'].getData();
    $.ajax({
        url: '/Admin/taiDuLieuLenServer',
        type: 'GET',
        dataType: 'json',
        data: { tradulieu: a },
        error: function (a) {
            if (a == "true") {
                alert("Thanh cong");
            }
            else {
                alert("Khong thanh cong");
            }
        }
    });
});
```

--phần lấy dữ liệu để riêng

```c#
 $('.SaveCkEditor').click(() => {
        var editorText = CKEDITOR.instances['editor'].getData();
    });
    $('.ViewCkEditor').click(() => {
        var editorText = CKEDITOR.instances['editor'].getData();
        $('#ViewDataCKEditor').html(editorText);
        $('.ContentPostViewAdmin').val(editorText);
    });
```

+Trong phần Controller

```c#
public JsonResult taiDuLieuLenServer(string tradulieu)
        {
            try
            {
                // dữ liệu bên trong sử lý
                return Json("true");
            }
            catch (Exception)
            {
                return Json("false");
            }

        }
```
