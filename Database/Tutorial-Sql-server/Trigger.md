# trigger

- trigger là một dạng đặc biệt của thủ tục lưu trữ , được thực thi một cách tự động khi có một sự thay đổi về dữ liệu

## đặc điểm

- Trigger chỉ thực thi tự động thông qua các sự kiện mà không thực thi bằng tay
- trigger sử dụng với khung nhìn
- Khi trigger thực thi theo các sự kiện Insert hoặc delete thì dữ liệu khi thay đổi sẽ được chuyển sang bảng inserted và deleted , là 2 bảng tạm thời chỉ có trong bộ nhớ tạm .
- các bảng này chỉ được sử dụng với các lệnh trigger
- các bảng này thường được sử dụng để khôi phục lại phần dữ liệu đã thay đổi roll back
- trigger chia thành 2 loại instead of và after
- instead of : là loại trigger mà hoạt động của sự kiện gọi trigger sẽ bị bỏ qua và thay vào đó là các lệnh trong trigger
- AFTER trigger là loại ngầm định , khác với instead of thì loại trigger này sẽ thực hiện các lệnh bên trong sau khi đã thực hiện xong , sự kiện kích hoạt trigger

## Các trường hợp sử dụng trigger

- sử dụng trigger khi các biện pháp bảo đảm toàn vẹn dữ liệu khác tkhoong đảm bảo được
- các công cụ này sẽ thực hiện kiểm tra tính toàn vẹn trước khi đưa vào csdl , còn trigger thực hiện kiểm tra tính toàn vẹn khi công việc đã thực hiện
- khi dữ liệu chưa được chuẩn hóa thì sẽ sảy ra trường hợp bị thừa , chứa ở nhiều vị trí khác nhau trong csdl thì yêu cầu cài đặt là dữ liệu cần cập nhật thống nhất ở mọi nơi
- trong trường hợp này ta phải sử dung trigger : khi sảy ra dây truyền dữ liệu giữa các bảng với nhau (khi dữ liệu bảng này thay đổi thì dữ liệu trong bảng khác cx được thay đổi theo)

## khả năng của trigger

- mỗn trigger có thể nhận biết ngăn chặn và hủy bỏ được những thao tác làm thay đổi trái phép dữ liệu trong csdl
- các thao tác trên dữ liệu (xóa cập nhật và bổ sung) có thể được trigger phát hiện ra và tự động thực hiện một loạt các thao tác khác trên csdl nhằm đảm bảo tính hợp lệ của dữ liệu
- thông qua trigger , ta có thể tạo và kiểm tra được mối quan hệ phức tạp hơn giữa các bảng trong csdl mà bản thân các ràng buộc không thể thực hiện được

## Định Nghĩa DML Trigger

cú pháp

```sql
create trigger  Tên_trigger
on Tên_Bảng
for {[insert][,][Update][,][delete]}
as
[if update(Tên cột)
[and update(Tên cột)\ or update(tên cột)]
]
các câu lệnh của trigger
```

Bảng :
Hoạt động | Bảng INSERTED | Bảng DELETED
INSERT | dữ liệu được insert | không có dữ liệu
DELETE | Không có dữ liệu | dữ liệu bị xóa
UPDATE | dữ liệu được cập nhật | dữ liệu trước cập nhật

```sql
create trigger T_Test
      on Test
      for insert
as
Begin
    declare @LengthTest int
    select @LengthTest = len(inserted.TestAge)
    from inserted
        if @LengthTest<=1
        print N'Tuổi Không Hợp lệ'
rollback tran
end
```

## DDL TRIGGER

- Một DDL trigger có thể được kích hoạt khi người dùng tạo 1 table hay drop table . ở cấp độ server DDL trigger có thể được kích hoạt khi có một tài khoản mới được tạo
- DDL trigger được lưu trữ trong csdl mà DDL trigger dduocj gắn vào . với server DDL trigger theo dõi các thay đổi được lưu trữ trong CSDL master với cấu trúc

```sql
Create trigger Tên_trigger
on {all server \ database}
for {loại sự kiện }[......,n]
as{các loại câu lệnh}
```

-- cái này không nên dùng nhé , dùng cái đầu tiên ý hé hé hé

## Enable/Disable TRIGGER

- trigger cần vô hiệu hóa trong một số trường hợp:
- Trigger gây ra lỗi trong qua trình sử lý csdl
- quá trình nhập hay khôi phục những dữ liệu không thỏa trigger
- Vô hiệu hóa trigger bằng lệnh DISABLE TRIGGER có cấu trúc :

```sql
DISABLE TRIGGER Tên_trigger
on { tên đối tượng | DATABASE | SERVER}
```
