-- class
```c#
public class AccessCached
    {
        private readonly ICacheBase cacheBase;
        public AccessCached(ICacheBase cacheBase)
        {
            this.cacheBase = cacheBase;
        }
        public List<T> GetList<T>(string Key, List<T> ts) where T : class
        {
            var key = CacheKey.GenCacheKey(Key);
            var listArticle = cacheBase.Get<List<T>>(key);
            if (listArticle == null)
            {
                cacheBase.Add(ts, key);
            }

            return listArticle;
        }
    }

 public class CacheKey
    {
        public static string GenCacheKey(string cacheName, params object[] args)
        {
            if (args != null && args.Length > 0)
            {
                string separator = "_";
                string cacheKey = cacheName;
                return args.Aggregate(cacheKey, (current, param) => current + (separator + (param.GetType() == typeof(string) ? SecurityProcess.MD5Hash(param.ToString()) : param)));
            }
            else return cacheName;
        }
}

/*  Cách sử dụng
     *  DI add như bình thường
     *  Khởi tạo new :
     *  private readonly static MemoryCache myCache = new MemoryCache(new MemoryCacheOptions());
     *  private ICacheBase _cache => new CacheMemoryHelper(myCache, true);
     *  private string _cacheKey;
     */
    public class CacheMemoryHelper : ICacheBase
    {
        private readonly IMemoryCache _cache;
        private readonly bool isEnableCache = false;
        public CacheMemoryHelper(IMemoryCache cache , bool _IsEnableCache)
        {
            this._cache = cache;
            this.isEnableCache = _IsEnableCache;
        }

        public void Add<T>(T o, string key)
        {
            if (isEnableCache)
            {
                // Look for cache key.
                if (!_cache.TryGetValue(key, out T _))
                {
                    // Key not in cache, so get data.
                    T cacheEntry = o;

                    // Set cache options.
                    var cacheEntryOptions = new MemoryCacheEntryOptions()
                        // Keep in cache for this time, reset time if accessed.
                        .SetAbsoluteExpiration(TimeSpan.FromSeconds(7200)); // 2h

                    // Save data in cache.
                    _cache.Set(key, cacheEntry, cacheEntryOptions);
                }
            }
        }

        public T Get<T>(string key)
        {
            return _cache.Get<T>(key);
        }

        public void Remove(string key)
        {
            _cache.Remove(key);
        }
    }

 public interface ICacheBase
    {
        T Get<T>(string key);
        void Add<T>(T o, string key);
        void Remove(string key);
    }
```

--- cách sử dụng

```c#
private readonly static MemoryCache myCache = new MemoryCache(new MemoryCacheOptions());
private ICacheBase _cache => new CacheMemoryHelper(myCache, true);
private string _cacheKey;
```