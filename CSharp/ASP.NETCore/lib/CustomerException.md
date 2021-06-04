```c#
public class CustomerException : Exception
    {
        public int errorCode;
        public CustomerException(int StatusCode , string message) :base(message)
        {
            errorCode = StatusCode;
        }
    }
```