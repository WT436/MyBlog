# Phân Trang Chia nhỏ dữ liệu để Hiển thị

```c#
#region lay tat ca san pham cua nha cung cap
        public static List<Product> layAllSanPhamCuaNhaCungCap(string Nhacc, int tab, ref int tong, int soBanGhi)
        {
            using (SellContext db = new SellContext())
            {
                try
                {
                    var a = db.Supplier.Where(n => n.NameUser == Nhacc).FirstOrDefault();
                    var avl = db.Product.Where(m => m.Supplier == a.Id);
                    tong = avl.Count() / soBanGhi + 1;
                    return avl.Skip((tab - 1) * soBanGhi).Take(soBanGhi).ToList();
                }
                catch (System.Exception)
                {
                    return null;
                }
            }
        }
#endregion
```

![image](https://user-images.githubusercontent.com/63473793/89185209-0dcbfc80-d5c4-11ea-90c7-6109eaf15c53.png)
