# Selector

- để xác định được mực tiêu để css có thể thực thi , nó có một cái gọi là Selector css (dịch ra tiếng việt nó là bộ trọn , nó đã nói nên tất cả )

- có 5 loại Selector Css là

## Simple selectors

- cái này vô cùng đơn giản : nó lựa trọn theo id name và class của html

```console
<style>
#IDnam{color:red}
.ClassNam{color:red}
</style>
<p id="IDnam" > Hainam </p>
<p class="ClassNam" > Hainam </p>
```

- lưu ý : với id cần có 1 dấu # , với class cần có 1 dấu .

## CSS Combinators

- một bộ chọn như thế này thì có thể kết hợp nhiều bộ chọn Simple selectors và cũng có thể kết hợp thêm
- bộ chọn con cháu (dấu cách)
- bộ chọn con (>)
- bộ chọn anh chị em kế cận (+)
- bộ chọn anh chị em chung (~)

1. Descendant Selector (bộ chọn con cháu )

- tức là sẽ lựa chọn các phần tử được thẻ đó bao bọc

2. Child Selector (bộ chọn con)

- tức là nó chỉ chọn những phần tử được nó bao bọc .......
- vd như thế này cho dễ hiểu

```console
<style>
div > p {
  background-color: yellow;
}
</style>
<div>
  <p>con 1</p>
  <p>con 2</p>
  <section>
        <p>cháu 1</p>
  </section>
  <p>con 4</p>
</div>
<p>ngang cấp</p>
```

- như chúng ta thấy cháu 1 và ngang cấp sẽ không đk to màu

3. CSS Pseudo-classes

- cái này thường được dùng tương tác với thẻ tự tìm kiếm nhé dễ ấy mà

4. CSS Pseudo

- Elements

```console
  ::after => p::after Chèn một cái gì đó sau nội dung của mỗi phần tử <p>
  ::before =>  p::before Chèn một cái gì đó trước nội dung của mỗi phần tử <p>
  ::first-letter =>  p::first-letter Chọn ký tự đầu tiên của mỗi phần tử <p>
  ::first-line =>  p::first-line Chọn dòng đầu tiên của mỗi phần tử <p>
  ::Selector =>  p::Selector Chọn phần của phần tử được chọn bởi người dùng
```

- Classes

```console
  :active =>  a:active Chọn liên kết hiện hoạt
  :checked =>  input:checked Chọn mọi phần tử <input> đã kiểm tra
  :disabled =>  input:disabled Chọn mọi phần tử <input> bị vô hiệu hoá
  :empty =>  p:empty Chọn mọi phần tử <p> không có phần tử con
  :enabled =>  input:enabled Chọn mọi phần tử <input> đã bật
  :first-child =>  p: first-child Chọn mọi phần tử <p> là phần tử con đầu tiên của cha mẹ của nó
  :first-of-type =>  p: first-of-type Chọn mọi phần tử <p> là phần tử <p> đầu tiên của nó
  :focus =>  input:focus Chọn phần tử <input> có tiêu điểm
  :hover =>  a: hover Chọn các liên kết khi di chuột qua
  :in-range =>  input:in-range Chọn các phần tử <input> có giá trị trong một phạm vi được chỉ định
  :invalid =>  input:invalid Chọn tất cả các phần tử <input> có giá trị không hợp lệ
  :lang (language) =>  p: lang (it) Chọn mọi phần tử <p> có giá trị thuộc tính lang bắt đầu bằng "it"
  :last-child =>  p: last-child Chọn mọi <p> ​​phần tử là phần tử con cuối cùng của cha mẹ của nó
  :last-of-type =>  p: last-of-type Chọn mọi phần tử <p> là phần tử <p> cuối cùng của phần tử chính của nó
  :link =>  a: link Chọn tất cả các liên kết chưa được truy cập
  :not =>  (selector): not (p) Chọn mọi phần tử không phải là phần tử <p>
  :nth-child =>  (n) p: nth-child (2) Chọn mọi phần tử <p> là phần tử con thứ hai của phần tử cha của nó
  :nth-last-child =>  (n) p: nth-last-child (2) Chọn mọi phần tử <p> là phần tử con thứ hai của phần tử cha của nó, tính từ phần tử cuối cùng
  :nth-last-of-type =>  (n) p: nth-last-of-type (2) Chọn mọi phần tử <p> là phần tử <p> thứ hai của phần tử cha
  của nó, tính từ phần tử con cuối cùng
  :nth-of-type =>  (n) p: nth-of-type (2) Chọn mọi phần tử <p> là phần tử <p> thứ hai của nó
  :only-of-type =>  p: only-of-type Chọn mọi phần tử <p> là phần tử <p> duy nhất của nó
  :only-child =>  p: only-child Chọn mọi phần tử <p> là phần tử con duy nhất của phần tử cha của nó
  :optional =>	input:optional Chọn các phần tử <input> không có thuộc tính "bắt buộc"
  :out-of-range =>  input: ngoài dải ô Chọn các phần tử <input> có giá trị bên ngoài một dải ô được chỉ định
  :read-only =>	input:read-only Chọn các phần tử <input> có chỉ định thuộc tính "chỉ đọc"
  :read-write =>  input: read-write Chọn các phần tử <input> không có thuộc tính "readonly"
  :required =>	input:required Chọn các phần tử <input> có chỉ định thuộc tính "bắt buộc"
  :root =>  root Chọn phần tử gốc của tài liệu
  :target =>  #news: target Chọn phần tử #news đang hoạt động hiện tại (được nhấp vào URL có chứa tên liên kết đó)
  :valid =>  input:valid Chọn tất cả các phần tử <input> có giá trị hợp lệ
  :visited =>  a:visited Chọn tất cả các liên kết đã truy cập
```

5. CSS [attribute] Selector

- bộ chọn được sử dụng để chọn các phần tử có thuộc tính được chỉ định.

nó gồm có :

```console
[attribute]
[attribute=value]
[attribute~=value]
[attribute|=value]
[attribute^=value]
[attribute$=value]
[attribute*=value]
```

-- đang tức tự đi mà tìm
