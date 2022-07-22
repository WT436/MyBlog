# Overflow

- Thuộc tính overflow xác định điều gì sẽ xảy ra nếu một thành phần box tràn nội dung.

```console
tag {
    overflow: giá trị;
}
- visible	overflow: visible;	 Khi chiều cao của box không đủ chứa text, thì text vẫn hiển thị tràn qua box, đây là mặc định.
- hidden	overflow: hidden;	 Khi chiều cao của box không đủ chứa text, thì text bị tràn sẽ được dấu đi.
- scroll	overflow: scroll;	 Khi chiều cao của box không đủ chứa text, thì text bị tràn sẽ được dấu đi và xuất hiện thanh scroll, khi cuộn sẽ hiển thị text.Khi sử dụng thành phần này sẽ xuất hiện cả thanh scroll ngang và dọc.
- auto	    overflow: auto;	     Khi chiều cao của box không đủ chứa text, thì thanh scroll sẽ tự động hiển thị.
_ Khi sử dụng thành phần này sẽ xuất hiện thanh scroll dọc.
- inherit	overflow: inherit;	 Xác định thừa hưởng thuộc tính từ thành phần cha (thành phần bao ngoài).
```
