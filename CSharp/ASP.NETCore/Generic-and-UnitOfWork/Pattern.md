# Generic-and-UnitOfWork sự kết hợp hoàn hảo giữa một lớp mà không cần chỉ ra đối số kiểu dữ liệu là gì và connect db

1. Generic : Generic trong C# cho phép bạn định nghĩa một hàm, một lớp mà không cần chỉ ra đối số kiểu dữ liệu là gì. Tuỳ vào kiểu dữ liệu mà người dùng truyền vào thì nó sẽ hoạt động theo kiểu dữ liệu đó. ... Khi bạn gọi cú pháp bên dưới thì hàm Swap sẽ chạy và thay ký tự T thành kiểu dữ liệu int tương ứng.
2. UnitOfWork : Unit Of Work là một khái niệm liên quan đến hiệu quả của việc triển khai Repository Pattern.

3. Tại sao : Unit Of Work được sử dụng để đảm bảo nhiều hành động như insert, update, delete...được thực thi trong cùng một transaction thống nhất. Nói đơn giản hơn, nghĩa là khi một hành động của người dùng tác động vào hệ thống, tất cả các hành động như insert, update, delete...phải thực hiện xong thì mới gọi là một transaction thành công. Gói tất cả các hành động đơn lẻ vào một transaction để đảm bảo tính toàn vẹn dữ liệu.

4. Tóm cái váy lại là cứ dùng đi , nó cool vcl ra nhá , tăng tốc độ code của bạn lên gọi là tốc độ tụt cả quần

# Bắt đầu ngôn ngữ sử dụng Csharp

## Bắt đầu với tầng thấp nhất : Data

- DemoDbContext : Class kết nối csdl

```c#
// cái này thì quá quen thuộc rồi
public class DemoDbContext : DbContext
    {
        public DemoDbContext(DbContextOptions<DemoDbContext> options) : base(options)
        { }

        public DbSet<Login> Login { get; set; }
        public DbSet<Product> Products { get; set; }

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
        }
    }
```

- Login và Product là 2 class hứng dữ liệu chả biết giải thích ntn , thôi thì tạo bừa đi

```c#
 public class Login
    {
        public int Id { get; set; }
        public string Title { get; set; }
        public string Content { get; set; }
        public DateTime CreatedDate { get; set; }

        public Login()
        {
            CreatedDate = DateTime.Now;
        }
    }

      public class Product
    {
        [Key]
        [DatabaseGenerated(DatabaseGeneratedOption.Identity)]
        public int Id { get; set; }
        public string Sku { get; set; }
        public string Name { get; set; }
        public int Price { get; set; }
        public DateTime CreatedDate { get; set; }

        public Product()
        {
            CreatedDate = DateTime.Now;
        }
    }
```

## Services : tầng khai báo mẫu cho Repository làm theo

- IRepository class này

```c#
 public interface IRepository<T> where T : class
    {
        DbSet<T> DbSet { get; } // truyền cho kiểu dữ liệu vào trong
        DemoDbContext DbContext { get; set; } //truyền cổng kết nối


        IEnumerable<T> GetAll();
        IEnumerable<T> GetMany(Expression<Func<T, bool>> predicate);
        //Expression<Func<T, bool>> predicate cái quần què này là kiểm tra linq
        // predicate = n=> n.id = "nam" chả hạn
        // hiểu đơn giản vd như nam.where(predicate) chả hạn
        //cuối sẽ có demo sau
        T GetById(int id);
        T Get(Expression<Func<T, bool>> predicate);
        IEnumerable<T> FromSqlQuery(string sql);


        void Add(T entity);
        void Delete(T entity);
        void DeleteRange(IEnumerable<T> entities);
        void Update(T entity);

        Task<IEnumerable<T>> GetAllAsync();
        Task<IEnumerable<T>> GetManyAsync(Expression<Func<T, bool>> predicate);
        Task<T> GetByIdAsync(int id);
        Task<T> GetAsync(Expression<Func<T, bool>> predicate);
        Task<IEnumerable<T>> FromSqlQueryAsync(string sql);
    }
```

## domain nơi thực thi , trái tim của hệ thống

- Tạo một Repositories class

```c#
public class Repository<T> : IRepository<T> where T : class
    {
        public Repository()
        {
        }
        public DemoDbContext DbContext { get; set; }
        public DbSet<T> DbSet // tác dung cả nó gọn đúng ko
        {
            get
            {
                return DbContext.Set<T>();
            }
        }


        public void Add(T entity)
        {
            DbSet.Add(entity);
        }

        public void Delete(T entity)
        {
            T existing = DbSet.Find(entity);
            if (existing != null)
                DbSet.Remove(existing);
        }

        public void DeleteRange(IEnumerable<T> entities)
        {
            DbSet.RemoveRange(entities);
        }

        public T GetById(int id)
        {
            return DbSet.FirstOrDefault(c =>
            ((int)c.GetType().GetProperty("Id").GetValue(c) == id));
        }
        public T Get(Expression<Func<T, bool>> predicate)
        {
            return DbSet.FirstOrDefault(predicate);
        }
        public IEnumerable<T> GetAll()
        {
            return DbSet.AsEnumerable();
        }
        public IEnumerable<T> GetMany(Expression<Func<T, bool>> predicate)
        {
            return DbSet.Where(predicate).AsEnumerable();
        }
        public void Update(T entity)
        {
            DbContext.Entry(entity).State = EntityState.Modified;
            DbSet.Attach(entity);
        }
        public IEnumerable<T> FromSqlQuery(string sql)
        {
                return DbSet.FromSqlRaw(sql).AsEnumerable();
                // nếu như cái thằng quần què FromSqlRaw nó méo chạy thì
                // add cái của khỉ này vào nhé : Microsoft.EntityFrameworkCore.Relational
        }
        public async Task<IEnumerable<T>> GetAllAsync()
        {
            var data = await DbSet.ToListAsync();
            return data;
        }
        public async Task<IEnumerable<T>> GetManyAsync(Expression<Func<T, bool>> predicate)
        {
            var data = await DbSet.Where(predicate).ToListAsync();
            return data;
        }
        public async Task<T> GetByIdAsync(int id)
        {
            var data = await DbSet.FirstOrDefaultAsync(c =>
            ((int)c.GetType().GetProperty("Id").GetValue(c) == id));
            return data;
        }
        public async Task<T> GetAsync(Expression<Func<T, bool>> predicate)
        {
            T data;
                data = await DbSet.FirstOrDefaultAsync(predicate);
            return data;
        }
        public async Task<IEnumerable<T>> FromSqlQueryAsync(string sql)
        {
            IEnumerable<T> data;
                data = await DbSet.FromSqlRaw(sql).ToListAsync();

            return data;
        }
    }
```

- tiếp tục add 1 class UnitOfWork

```c#
 public class UnitOfWork : IDisposable
    {
        public DemoDbContext DbContext { get; } //đây là class kết nối db của bạn

        public IRepository<Login> LoginRepository { get; } //khai báo đầy đủ nhé
        public IRepository<Product> ProductRepository { get; }

        public UnitOfWork(DemoDbContext context,//DI
             IRepository<Login> news,
             IRepository<Product> product)
        {
            DbContext = context;

            LoginRepository = news;
            LoginRepository.DbContext = DbContext;// truyền DB

            ProductRepository = product;
            ProductRepository.DbContext = DbContext;
        }

        public int SaveChanges()
        {
            var iResult = DbContext.SaveChanges();
            return iResult;
        }

        public async Task<int> SaveChangesAsync()
        {
            var iResult = await DbContext.SaveChangesAsync();
            return iResult;
        }

        public void Dispose()
        {
            DbContext.Dispose();
        }
    }
```

- đến phần quẩy rồi , đến đây check kiểu hay làm gì cx dk nhé ..... add class mẫu như sau DemoLogin

```c#
// ở đây cần cái gì thì gọi cái ấy ra , chứ ko phải gọi tất , đừng ngố như mình ngày  xưa
public class DemoLogin
    {
        private UnitOfWork unit;
        public DemoLogin(UnitOfWork _unit)
        {
            unit = _unit;
        }
        public void Add(Login entity)
        {
            unit.LoginRepository.Add(entity);
            unit.SaveChanges();
        }
        public IEnumerable<Login> GetAll()
        {
            var data = unit.LoginRepository.GetAll();
            return data;
        }
        public Login GetById(int id)
        {
            return unit.LoginRepository.GetById(id);
        }

        public Login Get(int a = 2)
        {
            return unit.LoginRepository.Get(n => n.Id == a);
            //Expression<Func<T, bool>> predicate nó đấy
        }
        public IEnumerable<Login> FromSqlQuery(int a = 3)
        {
           return unit.LoginRepository.FromSqlQuery($"SELECT * FROM Login WHERE id={a}");
        }
    }
```

# Họ Họ chưa khai báo DI kìa

```c#
            services.AddTransient<IRepository<Login>, Repository<Login>>();
            services.AddTransient<IRepository<Product>, Repository<Product>>();
            services.AddTransient<UnitOfWork>();//buộc có
```

- chả biết còn gì không , rồi mk sẽ update sau

# code mẫu https://github.com/WT436/Demo-Unit-Of-Work
