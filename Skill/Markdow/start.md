## Cơ bản và cú pháp của Markdown 

# Tiêu đề
```
# Header h1
## Header h2
### Header h3
#### Header h4
##### Header h5
###### Header h6
```
|Ví dụ|
| --- |
# Header h1
## Header h2
### Header h3
#### Header h4
##### Header h5
###### Header h6

---

### 🌟🌟 Hàng ngang 🌟🌟
```
____

---

***
```
|Ví dụ cho Hàng ngang|
| --- |
___
---
***

---

### 🌟🌟Nhấn mạnh từ ngữ 🌟🌟
```
**In đậm từ**

__TIn đậm từ__

*In nghiêng từ*

_In nghiêng từ_

~~Gạch ngang từ~~
~Gạch ngang từ~
```
|Ví dụ : Nhấn mạnh từ ngữ|
| --- |

**In đậm từ**

__TIn đậm từ__

*In nghiêng từ*

_In nghiêng từ_

~~Gạch ngang từ~~
---

### 🌟🌟 Trích dẫn 🌟🌟
```
> Trích dẫn đơn

> Trích dân ngoài
>> trích dẫn trong
>>> Trích dẫn trong 

```
|Ví dụ : Trích dẫn|
| --- |

> Trích dẫn đơn

> Trích dân ngoài
>> Trích dẫn trong
>>> Trích dẫn trong 
---

### 🌟🌟 Danh Sách 🌟🌟
```

Bất định : 
+ Bắt đầu một dòng với  `+`, `-`, hoặc `*`
+ Danh sách phụ được tạo bằng cách thụt lề 2 dấu cách:
  - Thay đổi ký tự đánh dấu buộc bắt đầu danh sách mới:
    * Danh sách con với *
    + Danh sách con với +
    - Danh sách con với -
+ Anh em triển nhanh thôi!

Tuần tự

1. Bắt đầu danh sách tuần tự
2. Tiếp nối danh sách tuần tự
3. Tiếp nối danh sách tuần tự

1. Vẫn nhận biết được số tuần tự
1. Kể cả việc tất cả con số là `1.` thì vẫn md vẫn nhận biết được

Con số khởi đầu

69. Con số khởi đầu ngẫu nhiên
1. Tự động nhận biết sau số khởi dầu

```
|Ví dụ : Danh Sách|
| --- |

Bất định : 
+ Bắt đầu một dòng với  `+`, `-`, hoặc `*`
+ Danh sách phụ được tạo bằng cách thụt lề 2 dấu cách:
  - Thay đổi ký tự đánh dấu buộc bắt đầu danh sách mới:
    * Danh sách con với *
    + Danh sách con với +
    - Danh sách con với -
+ Anh em triển nhanh thôi!

Tuần tự

1. Bắt đầu danh sách tuần tự
2. Tiếp nối danh sách tuần tự
3. Tiếp nối danh sách tuần tự

1. Vẫn nhận biết được số tuần tự
1. Kể cả việc tất cả con số là `1.` thì vẫn md vẫn nhận biết được

Con số khởi đầu

69. Con số khởi đầu ngẫu nhiên
1. Tự động nhận biết sau số khởi dầu
---

### 🌟🌟 Code 🌟🌟
```
Chỉ cần thêm cặp dấu ``
Nếu cần hiển thị thành khối thì dùng cặp dấu ``` data ```
Nếu cần hiển thị đúng định dạng ngôn ngữ thì thêm loại ngôn ngữ sau ``` đầu tiên  ```Javascript Console.log("Hế lô baby!") ```. 
Nhớ phải xuống dòng đấy
```
|Ví dụ : Code |
| --- |

`Nam` `True` `False` `java` `c#`

``` 
Console.log("Hế lô baby!") 
```

```js
Console.log("Hế lô baby!") 
```

---

### 🌟🌟 Bảng 🌟🌟
```

| Id | Value |
| ------ | ----------- |
| 1   | One |
| 2 | Two  |

Căn chỉnh theo cột dựa vào vị trí dâu :

| Id | Value trái | Value giữa | Value phải |
|-----| :---|:---:|---:|
| 1   | One |One |One |
| 2   | Two | Two | Two |

Hiển thị | dùng `\|`

| Id | Value |
| ------ | ----------- |
| 1   | One \| |
| 2 | Two  |

```
|Ví dụ : Bảng|
| --- |

| Id | Value |
| ------ | ----------- |
| 1   | One |
| 2 | Two  |

Căn chỉnh theo cột

| Id | Value trái | Value giữa | Value phải |
|-----| :---|:---:|---:|
| 1   | One |One |One |
| 2   | Two | Two | Two |

Hiển thị | dùng `\|`

| Id | Value |
| ------ | ----------- |
| 1   | One \| |
| 2 | Two  |

---

### 🌟🌟 Link - Đường dẫn 🌟🌟
```
[Tên Hiển thị](https://www.google.com/)

[Google](https://www.google.com/ "Chuyển đến google!")

Cho phép nhìn thấy dường dẫn : https://www.google.com/

```
|Ví dụ : Link - Đường dẫn|
| --- |

[Tên Hiển thị](https://www.google.com/)

[Google](https://www.google.com/ "Chuyển đến google!")

Cho phép nhìn thấy dường dẫn : https://www.google.com/

Liên kết đến đường dẫn tệp : [Đến 🌟🌟 Link - Đường dẫn 🌟🌟 ](#-link---đường-dẫn-)

---

### 🌟🌟 Link - Đường dẫn 🌟🌟
```

[Tên Hiển thị](https://www.google.com/)

[Google](https://www.google.com/ "Chuyển đến google!")

Cho phép nhìn thấy dường dẫn : https://www.google.com/

Liên kết đến đường dẫn tệp : [Đến 🌟🌟 Link - Đường dẫn 🌟🌟 ](#-link---đường-dẫn-)

Với ảnh bạn lên github vào bất kỳ 1 file `.md` nào và page ảnh sẽ có đường dẫn đến ảnh github repository 

![image](https://user-images.githubusercontent.com/63473793/168469375-4cf14536-d112-45bc-ba45-43ff87ff1333.png)

```
|Ví dụ : Link - Đường dẫn|
| --- |

[Tên Hiển thị](https://www.google.com/)

[Google](https://www.google.com/ "Chuyển đến google!")

Cho phép nhìn thấy dường dẫn : https://www.google.com/

Liên kết đến đường dẫn tệp : [Đến 🌟🌟 Link - Đường dẫn 🌟🌟 ](#-link---đường-dẫn-)

Với ảnh bạn lên github vào bất kỳ 1 file `.md` nào và page ảnh sẽ có đường dẫn đến ảnh github repository 

![image](https://user-images.githubusercontent.com/63473793/168469375-4cf14536-d112-45bc-ba45-43ff87ff1333.png)

---

<br/><b><i> Creator : WT436 - Trần Hữu Hải Nam </i></b>