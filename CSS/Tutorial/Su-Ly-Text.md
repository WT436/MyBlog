- gồm có các loại
- text-overflow
- word-wrap
- word-break
- writing-mode

## Text Overflow

- thuộc tính chỉ định cách báo hiệu nội dung bị tràn không được hiển thị cho người dùng.
- khi bị tràn nó sẽ ngắt và thay vào đó là ...
- clip : Mặc định cho thuộc tính này. Giá trị từ khóa này sẽ cắt bớt văn bản ở giới hạn của vùng nội dung, do đó, việc cắt bớt có thể xảy ra ở giữa một ký tự. Để cắt đoạn chuyển đổi giữa các ký tự, bạn có thể chỉ định text-tràn dưới dạng chuỗi trống, nếu điều đó được hỗ trợ trong các trình duyệt mục tiêu của bạn: text-tràn: '';.
- ellipsis : Giá trị từ khóa này sẽ hiển thị một dấu chấm lửng ('…') để biểu thị văn bản được cắt bớt. Dấu chấm lửng được hiển thị bên trong vùng nội dung, giảm lượng văn bản được hiển thị. Nếu không có đủ không gian để hiển thị dấu chấm lửng, nó sẽ bị cắt bớt.

## word-wrap

- Thuộc tính word-wrap trong CSS được sử dụng để ngắt một từ dài và quấn vào dòng tiếp theo. Nó xác định xem có nên ngắt các từ khi nội dung vượt quá ranh giới của vùng chứa nó hay không.

- word-wrap: normal|break-word|initial|inherit;
- normal: Đây là giá trị mặc định, Các dòng chỉ có thể được ngắt tại các điểm ngắt bình thường (dấu cách, ký tự không phải chữ và số, v.v.).
- break-word : Các từ vượt quá chiều rộng của vùng chứa sẽ được ngắt tùy ý để vừa với giới hạn của vùng chứa

## Word Breaking

- thuộc tính chỉ định các quy tắc ngắt dòng.

```console
  word-break: keep-all; Đoạn văn này chứa một số văn bản. Dòng này sẽ-ngắt ở-dấu gạch nối.
  word-break: break-all;Đoạn văn này chứa một số văn bản. Các dòng sẽ ngắt ở bất kỳ ký tự nào.
```

## Writing Mode

- thuộc tính chỉ định xem các dòng văn bản được bố trí theo chiều ngang hay chiều dọc.

```console
writing-mode: horizontal-tb;
writing-mode: vertical-rl;
writing-mode: vertical-rl;
```
