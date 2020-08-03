# Convert trên máy khách base64 cho đỡ nặng server

```html
<div class="gallery-grid">
  <a
    class="example-image-link"
    id="aimgTest1"
    href="~/images/default-img.png"
    data-lightbox="example-set"
  >
    <img id="imgTest1" src="~/images/default-img.png" alt="" />
    <div class="captn">
      <h4>Xem Chi Tiết ảnh chính</h4>
    </div>
  </a>
  <input
    id="inputFileToLoad1"
    type="file"
    onchange="encodeImageFileAsURL1();"
  />
  <input
    asp-for="anh1"
    id="inputFileToLoad11"
    type="text"
    style="display: none;"
    readonly="readonly"
  />
</div>
```

![image](https://user-images.githubusercontent.com/63473793/89135379-484b8000-d557-11ea-87fd-1743a8c1dae6.png)
![image](https://user-images.githubusercontent.com/63473793/89135397-7204a700-d557-11ea-86e3-b20e586f9431.png)

- code javascript

```javascript
function encodeImageFileAsURL1() {
  var filesSelected = document.getElementById("inputFileToLoad1").files;
  if (filesSelected.length > 0) {
    var fileToLoad = filesSelected[0];

    var fileReader = new FileReader();

    fileReader.onload = function (fileLoadedEvent) {
      var srcData = fileLoadedEvent.target.result; // <--- data: base64

      document.getElementById("imgTest1").src = srcData;
      document.getElementById("aimgTest1").href = srcData;
      document.getElementById("inputFileToLoad11").value = srcData;
    };
    fileReader.readAsDataURL(fileToLoad);
  }
}
```

![image](https://user-images.githubusercontent.com/63473793/89135408-8ea0df00-d557-11ea-8272-3dd3413d76b3.png)
