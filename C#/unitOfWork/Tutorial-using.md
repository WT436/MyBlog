Cài đặt : 
Entity là các class chứa kiểu dữ liệu như bình thường
```c#
  public partial class Address
    {
        public int Id { get; set; }
    }
```
Repository :
```c#
 public class AddressRepository : Repository<Address>, IRepository<Address>
    {
        public AddressRepository(AuthorizationContext dbContext) : base(dbContext)
        {

        }
    }
```

có 2 cách để cài đặt : 
1. Startup
``` c#
 services.AddDbContext<DbContext>(opt =>
            {
                opt.UseSqlServer(configuration["ConnectionStrings:DbContextStr"]);
            })
                    .AddUnitOfWork<DbContext>()
                    .AddCustomRepository<ExceptionLog, ExceptionLogRepository>()
            ;
```
2. 
``` c#
static IUnitOfWork<DbContext> unitOfWork = new UnitOfWork<DbContext>(new DbContext());
unitOfWork.GetRepository<class>().GetAllAsync();
```