Chúng Ta Đã có 1 file ntn  rồi :
![image](https://user-images.githubusercontent.com/63473793/89106177-e0f7d800-d451-11ea-8745-a8b8f5afef50.png)
Bây giờ sẽ clear nó cho dễ quản lý
+appsettings.json
{
  "ConnectionStrings": {
    "ConnectDatabaseContextString": "Chuỗi Kết Nối"
  }
}
* Đầu Tiên Chuyển Hêt file EF qua 1 Bên 
![image](https://user-images.githubusercontent.com/63473793/89107090-beb58880-d458-11ea-9084-58f27c9f9892.png)

* Kết Nối Đến File Json để lấy đoạn connect
![image](https://user-images.githubusercontent.com/63473793/89107115-f91f2580-d458-11ea-993e-1284db0a37af.png)
```c#
if (!optionsBuilder.IsConfigured)
            {
                IConfigurationRoot configuration = new ConfigurationBuilder()
                                               .SetBasePath(Directory.GetCurrentDirectory())
                                               .AddJsonFile("appsettings.json")
                                               .Build();
                var connectionString = configuration.GetConnectionString("ConnectDatabaseContextString");
                optionsBuilder.UseSqlServer(connectionString);
            }
```
* Nếu Muốn Chi Nhỏ File  nữa thì dùng cái này :
```c#
public class HuyenType : IEntityTypeConfiguration<Huyen>
    {
        public void Configure(EntityTypeBuilder<Huyen> builder)
        {
            builder.HasKey(e => e.Idqh)
                    .HasName("PK__Huyen__B87C32EAB8D5B201");

            builder.Property(e => e.Idqh)
                .HasColumnName("IDQH")
                .ValueGeneratedNever();

            builder.Property(e => e.Idtp).HasColumnName("IDTP");

            builder.Property(e => e.NameQh)
                .HasColumnName("NameQH")
                .HasMaxLength(300);

            builder.HasOne(d => d.IdtpNavigation)
                .WithMany(p => p.Huyen)
                .HasForeignKey(d => d.Idtp)
                .HasConstraintName("FK__Huyen__IDTP__267ABA7A");
        }
    }
```
và đặt trong class connect vừa tách lag 
```c#
modelBuilder.ApplyConfiguration(new HuyenType());
```
do mk lười nên làm vậy thui , mk nghĩ là nên sửa dụng như vậy vì thiết kế trên sql sử dụng câu lệnh sql bao giờ cx chuẩ xác hơn 
