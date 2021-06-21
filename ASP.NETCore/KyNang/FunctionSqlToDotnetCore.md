# Sử dụng funtion trong sql để lấy dữ liệu cho server

- code một function mẫu

```sql
go--**************************************************************************************
create function  DiscountHome()
returns @bang table(id int ,
			  ten nvarchar(100),
			  gia int ,
			  soluongconlai int ,
			  anh1 nvarchar(max),
			  sosao int ,
			  phantram int )
as
begin
insert into @bang select Product.id,Product.ten,Product.gia,Product.SoLuongCoSan as soluongconlai,
						ImageProduct.anh1,Evaluate.sosao, Discount.phantram
	from Product
	inner join ImageProduct on Product.ImageProduct = ImageProduct.id
	inner join categoryProduct on Product.categoryProduct= categoryProduct.id
	inner join ThemeProduct on categoryProduct.Theme = ThemeProduct.id
	left join (select sum(sosao)as sosao, Product  from Evaluate group by Product) as Evaluate on Product.id = Evaluate.Product
	left join ProductUsingDiscount on ProductUsingDiscount.Product = Product.id
	left join Discount on Discount.id=ProductUsingDiscount.Discount
	where Discount.phantram >10 and Product.Isdelete=0
	order by Discount.phantram asc
return
end
```

![image](https://user-images.githubusercontent.com/63473793/89185977-53d59000-d5c5-11ea-8d4e-ee7fe8a8da36.png)

- tạo một class để hứng dữ liệu trả ra

```c#
public class DiscountViewHomeContainer
    {
        public  int id {get; set;}
        public  string ten {get; set;}
        public  int gia {get; set;}
        public  int soluongconlai { get; set;}
        public string anh1  {get; set;}
        public  int sosao  {get; set;}
        public  int phantram { get; set;}
    }
    //lưu ý các trường dữ liệu phải đúng kiểu đúng thứ tự được trả ra từ sql
```

![image](https://user-images.githubusercontent.com/63473793/89186122-8e3f2d00-d5c5-11ea-8ef8-373b215627b8.png)

```c#
public virtual DbSet<DiscountViewHomeContainer> DiscountViewHomeContainer { get; set; }
// phần này được add trong class kết nối csdl ở đây là SellContext : DbContext
```

- cuối cùng gọi hàm hưng dữ liệu được trả ra

```c#
var a = db.DiscountViewHomeContainer.FromSqlRaw("select * from DiscountHome()").ToList();
//select * from DiscountHome() là câu lệnh sql nhé dùng như bình thường truyền tham số như bt
```
