```c#
 public static class MappingData
    {
        public static Mapper InitializeAutomapper()
        {
            var config = new MapperConfiguration(cfg =>
            {
                cfg.CreateMap<AccountDtos,UserProfile>()
                   .ForMember(dest => dest.FirstName, act => act.MapFrom(src => src.First_name))
                   .ForMember(dest => dest.LastName, act => act.MapFrom(src => src.Last_name))
                   .ForMember(dest => dest.FullName, act => act.MapFrom(src => src.Full_name))
            });
            var mapper = new Mapper(config);
            return mapper;
        }
    }
```
sử dụng

```c#
private readonly Mapper mapper = MappingData.InitializeAutomapper();

var user_profile = mapper.Map<UserProfile>(accountDto);

```