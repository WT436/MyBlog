```c#
 public class ProcessExceptionFilterAttribute : IExceptionFilter
    {
        private  IApiLogger _logger => new  ApiLogger();

        public void OnException(ExceptionContext context)
        {
            context.ExceptionHandled = true;
            HttpResponse response = context.HttpContext.Response;
            switch (context.Exception)
            {
                //Lỗi Từ Phía Client
                case CustomerException e: // 400
                    response.StatusCode = e.errorCode;
                    context.Result = new ObjectResult(context.Exception.Message);
                    break;
                case KeyNotFoundException e: // 400
                    context.Result = new ObjectResult(context.Exception.Message);
                    break;
                default:
                    // Error server
                    response.StatusCode = (int)HttpStatusCode.InternalServerError;
                    InfomationError infomationError = new InfomationError
                    {
                        Exception = context.Exception,
                        ServerError = "Login API",
                        AccountCreate = 1,
                        IpAccount = context.HttpContext.Connection.RemoteIpAddress.ToString(),
                        Level = "Error"
                    };

                    _logger.LogError(infomationError);
                    context.Result = new ObjectResult("Server error occurred.");
                    break;
            }
            response.ContentType = "application/json";
        }
    }
```