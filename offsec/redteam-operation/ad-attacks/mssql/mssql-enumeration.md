# MSSQL Enumeration

## MSSQL Enumeration

### Server name

```csharp
SELECT srvname from master..sysservers
```

![](../../../../.gitbook/assets/image%20%28296%29.png)

### Check available Usernames

```csharp
SELECT name FROM sys.syslogins
SELECT name FROM sys.server_principals
```

```csharp
SELECT SUSER_NAME()

SELECT SUSER_NAME(1)

select * from master.sys.server_principals
```



