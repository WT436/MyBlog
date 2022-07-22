# background

- Thuộc tính CSS viết tắt nền đặt tất cả các thuộc tính kiểu nền cùng một lúc, chẳng hạn như màu sắc, hình ảnh, nguồn gốc và kích thước hoặc phương pháp lặp lại.

- background có các loại như sau
- background-attachment
- background-clip
- background-color
- background-image
- background-origin
- background-position
- background-repeat
- background-size
- background

- chúng ta sẽ tìm hiểu từng thứ một nhé :

## background

- Syntax

```css
/* sử dụng  <background-color> */
background: green;

/* sử dụng <bg-image> và <repeat-style> */
background: url("test.jpg") repeat-y;

/* sử dụng <box> và <background-color> */
background: border-box red;

/* Một hình ảnh duy nhất, căn giữa và chia tỷ lệ */
background: no-repeat center/80% url("/img/hainam.png");
```

- như chúng ta đã thấy background có thể sử dụng tất cả các thuộc tính của con nó và nó chính là cha của chúng , để sử dụng chi tiets chúng ta có thể sử dụng các background con

- background được chỉ định là một hoặc nhiều lớp nền, được phân tách bằng dấu phẩy.
- để hiểu hơn các thuộc tính con của nó chúng ta nên tìm hiểu các thành phần tạo nên nó trước

## background-attachment

- cấu trúc

```console
background-attachment: scroll;
background-attachment: fixed;
background-attachment: local;
background-attachment: inherit;
background-attachment: initial;
background-attachment: unset;
```

trong đó :

- fixed : Nền được cố định so với khung nhìn. Ngay cả khi một phần tử có cơ chế cuộn, nền sẽ không di chuyển theo phần tử đó.
- local : Nền được cố định so với nội dung của phần tử. Nếu phần tử có cơ chế cuộn, nền sẽ cuộn theo nội dung của phần tử và vùng sơn nền và vùng định vị nền có liên quan đến vùng có thể cuộn của phần tử hơn là với đường viền đóng khung chúng.
- scroll : Nền được cố định so với bản thân phần tử và không cuộn theo nội dung của nó. (Nó được gắn vào đường viền của phần tử một cách hiệu quả.)
- initial : đưa về mặc định của nó
- inherit : Kế thừa từ phần tử mẹ của nó

## background-clip

- Thuộc tính CSS background-clip đặt xem nền của phần tử có mở rộng bên dưới hộp viền, hộp đệm hay hộp nội dung hay không.
- cấu trúc

```console
background-clip: border-box;
background-clip: padding-box;
background-clip: content-box;
background-clip: text;
background-clip: inherit;
background-clip: initial;
background-clip: unset;
```

Trong đó :

- border-box : Nền kéo dài đến mép ngoài của đường viền (nhưng bên dưới đường viền theo thứ tự z).
- padding-box : Nền mở rộng ra mép ngoài của phần đệm. Không có nền nào được vẽ bên dưới đường viền.
- content-box : Nền được vẽ bên trong (cắt vào) hộp nội dung.
- text : Nền được vẽ bên trong (cắt vào) văn bản nền trước.

## background-color

- Thuộc tính CSS background-color đặt màu nền của một phần tử.
- như đã có 3 dạng chọn màu nên cơ bản

## background-image

- Thuộc tính CSS background-image đặt một hoặc nhiều hình nền trên một phần tử.

## background-origin

- Thuộc tính CSS background-origin đặt nguồn gốc của nền: từ phần đầu của đường viền, bên trong đường viền hoặc bên trong phần đệm.

cấu trúc :

```console
background-origin: border-box; Nền được định vị so với hộp viền.
background-origin: padding-box; Nền được định vị so với hộp đệm.
background-origin: content-box; Nền được đặt so với hộp nội dung.
```

## background-position

```console
Giá trị từ khóa
background-position: top;
background-position: bottom;
background-position: left;
background-position: right;
background-position: center;
giá trị <percentage>
background-position: 25% 75%;
các giá trị <length>
background-position: 0 0;
background-position: 1cm 2cm;
background-position: 10ch 8em;
Nhiều hình ảnh
background-position: 0 0, center;
Giá trị hiệu số cạnh
background-position: bottom 10px right 20px;
background-position: right 3em bottom 10px;
background-position: bottom 10px right;
background-position: top right 10px;
Giá trị toàn cầu
background-position: inherit;
background-position: initial;
background-position: unset;
```

## background-position-x

- Thuộc tính CSS background-position-x đặt vị trí ngang ban đầu cho mỗi hình nền. Vị trí có liên quan đến lớp vị trí được đặt theo gốc-nền.

```console
background-position-x: left;
background-position-x: center;
background-position-x: right;
```

## background-position-y

- Thuộc tính CSS background-position-y đặt vị trí dọc ban đầu cho mỗi hình nền. Vị trí có liên quan đến lớp vị trí được đặt theo gốc-nền.

```console
background-position-y: top;
background-position-y: center;
background-position-y: bottom;
```

## background-repeat

- background-repeat đặt cách hình ảnh nền được lặp lại. Hình nền có thể được lặp lại dọc theo trục ngang và trục dọc hoặc hoàn toàn không lặp lại.

```console
background-repeat: repeat-x;
background-repeat: repeat-y;
background-repeat: repeat; Hình ảnh được lặp lại nhiều đến mức cần thiết để bao phủ toàn bộ khu vực vẽ ảnh nền. Hình ảnh cuối cùng sẽ được cắt bớt nếu nó không vừa.
background-repeat: space; Hình ảnh được lặp lại nhiều nhất có thể mà không cần cắt bớt. Hình ảnh đầu tiên và cuối cùng được ghim vào hai bên của phần tử và khoảng trắng được phân bổ đồng đều giữa các hình ảnh. Thuộc tính background-position bị bỏ qua trừ khi chỉ có thể hiển thị một hình ảnh mà không cần cắt bớt. Trường hợp duy nhất xảy ra việc cắt bớt khi sử dụng không gian là khi không có đủ chỗ để hiển thị một hình ảnh.
background-repeat: round; Khi không gian cho phép tăng kích thước, các hình ảnh lặp lại sẽ kéo dài (không để lại khoảng trống) cho đến khi có chỗ (khoảng trống còn lại> = một nửa chiều rộng hình ảnh) để thêm một hình khác. Khi hình ảnh tiếp theo được thêm vào, tất cả những hình ảnh hiện tại sẽ nén lại để còn chỗ. Ví dụ: Một hình ảnh có chiều rộng ban đầu là 260px, được lặp lại ba lần, có thể kéo dài cho đến khi mỗi lần lặp lại có chiều rộng 300px và sau đó một hình ảnh khác sẽ được thêm vào. Sau đó, chúng sẽ nén thành 225px.
background-repeat: no-repeat; Hình ảnh không bị lặp lại (và do đó vùng sơn hình nền không nhất thiết sẽ bị che hoàn toàn). Vị trí của hình nền không lặp lại được xác định bởi thuộc tính CSS background-position.
```

## background-size

- thuộc tính đặt kích thước của hình nền của phần tử. Hình ảnh có thể được để ở kích thước tự nhiên, kéo dài hoặc hạn chế để phù hợp với không gian có sẵn.

```console
-- Giá trị từ khóa
background-size: cover;
background-size: contain;
-- Cú pháp một giá trị
background-size: 50%;
background-size: 3.2em;
background-size: 12px;
background-size: auto;
```

- Thuộc tính kích thước nền được chỉ định theo một trong những cách sau:
- Sử dụng các giá trị từ khóa chứa hoặc bao hàm.
- Chỉ sử dụng giá trị chiều rộng, trong trường hợp đó chiều cao được mặc định là tự động.
- Sử dụng cả giá trị chiều rộng và chiều cao, trong trường hợp này giá trị thứ nhất đặt chiều rộng và giá trị thứ hai đặt chiều cao.
- Mỗi giá trị có thể là <length>, <percentage> hoặc auto.
- Để chỉ định kích thước của nhiều hình nền, hãy phân tách giá trị cho mỗi hình nền bằng dấu phẩy.

### trên là một vài thành phần cơ bản của background , những phần tuyến tính CÓ THỂ sẽ push lên cũng có thể không :))
