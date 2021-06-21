```c#
 public class CacheResourceAttribute : TypeFilterAttribute
    {
        public CacheResourceAttribute()
            : base(typeof(CacheResourceFilter))
        {
        }
    }
```

```c#
public class CacheResourceFilter : IResourceFilter
    {
        private readonly static MemoryCache myCache = new MemoryCache(new MemoryCacheOptions());
        private ICacheBase _cache => new CacheMemoryHelper(myCache, true);
        private string _cacheKey;

        public void OnResourceExecuting(ResourceExecutingContext context)
        {
            //svc = context.HttpContext.RequestServices;
            //_cache = svc.GetService<ICacheBase>();

            _cacheKey = context.HttpContext.Request.Path.ToString();

            if (_cache.Get<string>(_cacheKey) is string cachedValue)
            {
                context.Result = new ContentResult()
                { Content = cachedValue };
            }
        }

        public void OnResourceExecuted(ResourceExecutedContext context)
        {
            IActionResult result = context.Result;
            if (result != null)
            {
                if (result is JsonResult json && json.StatusCode==200)
                {
                    _cache.Add(json.Value, _cacheKey);
                }

                if (result is ObjectResult obr && obr.StatusCode == 200)
                {
                    _cache.Add(obr.Value, _cacheKey);
                }
            }
        }
    }
```