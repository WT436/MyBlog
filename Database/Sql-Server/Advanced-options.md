# Advanced options (Thành phần nâng cao)

1. Bật và hiển thị các tùy chọn nâng cao

```
Exec sp_configure 'show advanced options' ,1
RECONFIGURE
GO
-- Show all configure
sp_configure
```

2. Bật mặc định nén sao lưu

```
Exec sp_configure 'backup compression default',1
GO
RECONFIGURE;
```

3. Đặt phần trăm hệ số lấp đầy mặc định

```
sp_configure 'fill factor', 100;
GO
RECONFIGURE;
```
4. Đặt khoảng thời gian khôi phục hệ thống

```
USE master;
GO
-- Set recovery every 3 min
EXEC sp_configure 'recovery interval', '3';
RECONFIGURE WITH OVERRIDE;
```

5. Enable cmd permission

```
EXEC sp_configure 'xp_cmdshell', 1
GO
RECONFIGURE
```

6. Đặt kích thước bộ nhớ máy chủ tối đa

```
USE master
EXEC sp_configure 'max server memory (MB)', 64
RECONFIGURE WITH OVERRIDE
```

7. Đặt số lượng nhiệm vụ điểm kiểm tra

```
EXEC sp_configure "number of checkpoint tasks", 4
```
