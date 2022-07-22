## Từ khóa this

- Từ khóa this được dùng để tham chiếu đến thể hiện hiện hành của một đối tượng. Tham
  chiếu this này được xem là con trỏ ẩn đến tất các phương thức không có thuộc tính tĩnh
  trong một lớp. Mỗi phương thức có thể tham chiếu đến những phương thức khác và các
  biến thành viên thông qua tham chiếu this này.

Tham chiếu this này được sử dụng thường xuyên theo ba cách:

Sử dụng khi các biến thành viên bị che lấp bởi tham số đưa vào, như trường hợp sau:

```c#
public void SetYear(int Nam) { this.Nam = Nam; }
```

Như trong đoạn mã trên phương thức SetYear sẽ thiết lập giá trị của biến thành viên
Nam, tuy nhiên do tham số đưa vào có tên là Nam, trùng với biến thành viên, nên ta phải
dùng tham chiếu this để xác định rõ các biến thành viên và tham số được truyền vào.

Khi đó this.Nam chỉ đến biến thành viên của đối tượng, trong khi Nam chỉ đến tham số.

Sử dụng tham chiếu this để truyền đối tượng hiện hành vào một tham số của một phương
thức của đối tượng khác:

```c#
public void Method1( OtherClass otherObject ) {
    // Sử dụng tham chiếu this để truyền tham số là bản thân đối tượng đang thực hiện.
    otherObject.SetObject( this );
    }
```

Như trên cho thấy khi cần truyền một tham số là chính bản thân của đối tượng đang thực
hiện thì ta bắt buộc phải dùng tham chiếu this để truyền.

Các thứ ba sử dụng tham chiếu this là mảng chỉ mục (indexer), phần này sẽ được trình
bày chi tiết trong bài sau.
