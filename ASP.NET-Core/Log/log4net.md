# Tầm quan trọng

LOG4NET là một thư viện mã nguồn mở cho phép chúng ta tạo ra một hoặc nhiều tập tin log, kiểu log cũng như nội dung log một cách linh hoạt và thuận tiện. Ngoài ra, Log4net còn có thể thay đổi trạng thái log lúc ứng dụng đang chạy mà không cần ngừng chương trình. Bên cạnh đó, khi sử dụng log4net sẽ không ảnh hưởng đáng kể đến performance của ứng dụng và điều quan trọng của một thư viện nguồn mở đó là chúng ta có thể tùy ý phát triển theo nhu cầu của cá nhân hoặc tập thể miễn là phù hợp giấy phép mã nguồn mở.

## Cài đặt theo class riêng

1. Cài đặt thư viện Install-Package log4net
2. Cài đặt theo class

- Tạo ILoggerManager

```c#
  public interface ILoggerManager
    {
        void LogInformation(string message);
        void LogWanning(string message);
        void LogError(string message, Exception exception);
    }
```

- LoggerManager

```c#
 public class LoggerManager : ILoggerManager
    {
        private readonly ILog _logger = LogManager.GetLogger(typeof(LoggerManager));
        public LoggerManager()
        {
            try
            {
                XmlDocument log4netConfig = new XmlDocument();

                using (var fs = File.OpenRead("log4net.config"))
                {
                    log4netConfig.Load(fs);

                    var repo = LogManager.CreateRepository(
                            Assembly.GetEntryAssembly(),
                            typeof(log4net.Repository.Hierarchy.Hierarchy));

                    XmlConfigurator.Configure(repo, log4netConfig["log4net"]);

                    // The first log to be written
                    _logger.Info("Log System Initialized");
                }
            }
            catch (Exception ex)
            {
                _logger.Error("Error", ex);
            }
        }

        public void LogError(string message, Exception exception)
        {
            _logger.Error(message, exception);
        }

        // Logging functionality happens here
        public void LogInformation(string message)
        {
            _logger.Info(message);
        }

        public void LogWanning(string message)
        {
            _logger.Info(message);
        }
    }
```

3. DI

```c#
 services.AddSingleton<ILoggerManager, LoggerManager>();
```

4. (nếu cần thiết) Ghi log khởi chạy server

```c#
 public static void Main(string[] args)
        {
            var host = CreateHostBuilder(args).Build();

            var logger = host.Services.GetRequiredService<ILoggerManager>();

            logger.LogInformation("Starting the Host");

            host.Run();
        }
```

5. Tạo 1 file log4net.config

```xml
<?xml version="1.0" encoding="utf-8" ?>
<log4net>
	<appender name="RollingLogFileAppender"
		type="log4net.Appender.RollingFileAppender">
		<lockingModel type="log4net.Appender.FileAppender+MinimalLock"/>
		<file value="Logs\" />
		<datePattern value="yyyy-MM-dd.'txt'"/>
		<staticLogFileName value="false"/>
		<appendToFile value="true"/>
		<rollingStyle value="Date"/>
		<maxSizeRollBackups value="100"/>
		<maximumFileSize value="15MB"/>
		<layout type="log4net.Layout.PatternLayout">
			<conversionPattern
			  value="%date [%thread] %-5level App  %newline %message %newline %newline"/>
		</layout>
	</appender>
	<root>
		<level value="ALL"/>
		<appender-ref ref="RollingLogFileAppender"/>
	</root>
</log4net>
```

## Cấu hình chi tiết cho file file log4net.config

1. Cấu trúc một file cấu hình log4net

```xml
<!-- Đây là thư mục gốc của tập tin cấu hình của bạn -->
<configuration>
  <!-- Phần này nên giữ nguyên -->
  <configSections>
    <section name="log4net"
      type="log4net.Config.Log4NetConfigurationSectionHandler, log4net"/>
  </configSections>

  <!-- Nội dung cấu hình -->
  <log4net> <!-- Level 1 -->
    <!-- Định nghĩa Các appender-->
    <appender>  <!-- Level 2 -->
      <layout>  <!-- Level 3 -->
        <conversionPattern />  <!-- Level 4 -->
      </layout>
      <filter>  <!-- Level 3 -->
      </filter>
    </appender>

    <!-- Sử dụng các appender-->
    <root> <!-- Level 2 -->
      <level /> <!-- Level 3 -->
      <appender-ref /> <!-- Level 3 -->
    </root>

</configuration>
```

- Thẻ <appender>

Thẻ này quy định các thức thể hiện(lưu trữ) các dòng log, trong đó có 4 cách cơ bản thể hiện: ConsoleAppender, FileAppender, RollingFileAppender, AdoNetAppender, … Cách hay dùng nhất là RollingFileAppender. Hãy để ý thẻ <layout>, xem bảng cuối bài để hiểu các thuộc tính.

2. RollingFileAppender

```XML
<!--Tạo ra tập tin log, khi tập tin này quá giới hạn thì nó sẽ bị đổi tên và tạo tập tin mới để log, vậy chúng ta sẽ có nhiều tập tin log.-->
<appender name="RollingFileAppender" type="log4net.Appender.RollingFileAppender">
 <file value="mylogfile.txt" />
<pre> <appendToFile value="true" />
 <rollingStyle value="Size" />
 <maxSizeRollBackups value="5" />
 <maximumFileSize value="10MB" />
 <staticLogFileName value="true" />
 <layout type="log4net.Layout.PatternLayout">
 <conversionPattern value="%date [%thread] %level %logger - %message%newline" />
 </layout>
</appender>
```

3. ConsoleAppender

```XML
<!--log ra màng hình, chỉ hiển thị khi ứng dụng có của sổ Console-->
<appender name="ConsoleAppender" type="log4net.Appender.ConsoleAppender">
  <layout type="log4net.Layout.PatternLayout">
    <conversionPattern value="%date{ABSOLUTE} [%thread] %level %logger - %message%newline"/>
  </layout>
  <filter type="log4net.Filter.StringMatchFilter">
    <stringToMatch value="test" />
  </filter>
  <filter type="log4net.Filter.DenyAllFilter" />
</appender>
```

4. FileAppender

```XML
<!--tạo ra duy nhất một file log-->
<appender name="FileAppender" type="log4net.Appender.FileAppender">
  <file value="mylogfile.log" />
  <appendToFile value="true" />
  <lockingModel type="log4net.Appender.FileAppender+MinimalLock" />
  <layout type="log4net.Layout.PatternLayout">
    <conversionPattern value="%date [%thread] %level %logger - %message%newline" />
  </layout>
  <filter type="log4net.Filter.LevelRangeFilter">
    <levelMin value="INFO" />
    <levelMax value="FATAL" />
  </filter>
</appender>
```

5. AdoNetAppender

```XML
<!--tạo ra các dòng log và lưu vào Database-->
<appender name="AdoNetAppender" type="log4net.Appender.AdoNetAppender">
  <bufferSize value="100" />
  <connectionType value="System.Data.SqlClient.SqlConnection,
   System.Data, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
  <connectionString value="data source=[database server];
    initial catalog=[database name];integrated security=false;
    persist security info=True;User ID=[user];Password=[password]" />
  <commandText value="INSERT INTO Log ([Date],[Thread],[Level],[Logger],
    [Message],[Exception]) VALUES (@log_date, @thread, @log_level,
    @logger, @message, @exception)" />
  <parameter>
    <parameterName value="@log_date" />
    <dbType value="DateTime" />
    <layout type="log4net.Layout.RawTimeStampLayout" />
  </parameter>
  <parameter>
    <parameterName value="@thread" />
    <dbType value="String" />
    <size value="255" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%thread" />
    </layout>
  </parameter>
  <parameter>
    <parameterName value="@log_level" />
    <dbType value="String" />
    <size value="50" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%level" />
    </layout>
  </parameter>
  <parameter>
    <parameterName value="@logger" />
    <dbType value="String" />
    <size value="255" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%logger" />
    </layout>
  </parameter>
  <parameter>
    <parameterName value="@message" />
    <dbType value="String" />
    <size value="4000" />
    <layout type="log4net.Layout.PatternLayout">
      <conversionPattern value="%message" />
    </layout>
  </parameter>
  <parameter>
    <parameterName value="@exception" />
    <dbType value="String" />
    <size value="2000" />
    <layout type="log4net.Layout.ExceptionLayout" />
  </parameter>
</appender>
```

## Ý nghĩa các thẻ

1. Layout

```XML
<!-- Đây là thẻ mô tả cách hiển thị một dòng log -->
<layout type="log4net.Layout.PatternLayout">
      <!-- Thẻ này là định dạng của một dòng log, ý nghĩa các ký tự xin tham khảo bảng cuối trang-->
      <conversionPattern value="%date [%thread] %-5level %logger [%ndc] - %message%newline"/>
</layout>
```

2. Filter

```XML
<!-- Thẻ này dùng để lọc log-->
<!-- Start-->
<!-- Chỉ log nếu dòng log có chữ test, chú ý rằng StringMatchFilter luôn đi kèm DenyAllFilter-->
<filter type="log4net.Filter.StringMatchFilter">
  <stringToMatch value="test" />
</filter>
<filter type="log4net.Filter.DenyAllFilter"/>
<!-- End-->

<!-- Chỉ log trong một giới hạn level-->
<filter type="log4net.Filter.LevelRangeFilter">
  <levelMin value="INFO" />
  <levelMax value="FATAL" />
</filter>

<!-- Start-->
<!-- Chỉ log level ERROR, chú ý rằng LevelMatchFilterluôn đi kèm DenyAllFilter-->
<filter type="log4net.Filter.LevelMatchFilter">
  <levelToMatch value="ERROR"/>
</filter>
<filter type="log4net.Filter.DenyAllFilter"/>
<!-- End-->

<!-- Dùng chung với hai trường hợp kể trên-->
<filter type="log4net.Filter.DenyAllFilter"/>
```

## Level log

Chúng ta có bảy level sau với mức cao nhất ở trên cùng của danh sách, khi bạn chọn một level để log thì các level từ đó trở lên đều được log:

- OFF – không có gì được log
- FATAL
- ERROR
- WARN
- INFO
- DEBUG
- ALL – mọi thứ sẽ được log

![image](https://user-images.githubusercontent.com/63473793/138235795-0511745f-09c0-456a-8eed-82f5816b11c5.png)

- Thẻ <Root>

```XML
<root>
  <level value="INFO"/> <!-- Chỉ log từ level INFO trở lên-->
  <appender-ref ref="FileAppender"/> <!-- dùng FileAppender-->
  <appender-ref ref="ConsoleAppender"/><!-- dùng ConsoleAppender-->
</root>
```

## Các thành phần chuyển đổi

```
    - %date : nhập ngày bằng cách sử dụng thông tin múi giờ địa phương. Ngày này có thể được định dạng bằng cách sử dụng dấu ngoặc nhọn và một mẫu bố cục, chẳng hạn như %date{MMMM dd, yyyy HH:mm:ss, fff} để xuất ra giá trị của “January 01, 2011 14:15:43, 767”. Tuy nhiên, bạn nên sử dụng một trong các định dạng ngày log4net (ABSOLUTE, DATE, or ISO8601) vì chúng mang lại hiệu suất tốt hơn.

    - %utcdate : Điều này giống với công cụ sửa đổi% date, nhưng nó xuất ra theo giờ quốc tế. Các bổ ngữ cho ngày / giờ đều hoạt động theo cùng một cách.

    - %exception : Nếu một ngoại lệ được chuyển vào, nó sẽ được nhập và một dòng mới sẽ được đặt sau ngoại lệ. Nếu không có ngoại lệ nào được đưa vào, mục nhập này sẽ bị bỏ qua và không có dòng mới nào được đưa vào. Dòng này thường được đặt ở cuối mục nhập nhật ký và thường một dòng mới cũng được đặt trước ngoại lệ.

    - %level :  Đây là cấp bạn đã chỉ định cho sự kiện  (DEBUG, INFO, WARN, etc.).

    - %message  : Đây là thông báo bạn đã chuyển vào sự kiện nhật ký.

    - %newline : Đây là một mục nhập dòng mới. Dựa trên nền tảng mà bạn đang sử dụng ứng dụng, điều này sẽ được dịch sang (các) ký tự dòng mới thích hợp. Đây là phương pháp ưa thích để nhập một dòng mới và nó không có vấn đề về hiệu suất so với các toán tử dành riêng cho nền tảng.

    - %timestamp : Đây là số mili giây kể từ khi bắt đầu ứng dụng.

    - %thread : Điều này sẽ cung cấp cho bạn tên của chuỗi mà mục nhập được thực hiện trên đó (hoặc số nếu chuỗi không được đặt tên).
```

v.v.v.vv. Cập nhật sau
