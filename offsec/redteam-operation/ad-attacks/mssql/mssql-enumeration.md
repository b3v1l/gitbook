# MSSQL Enumeration

## MSSQL Enumeration

### Server name

```csharp
SELECT srvname from master..sysservers
```

![](../../../../.gitbook/assets/image%20%28296%29.png)

### Check available Usernames

```csharp
SELECT SUSER_NAME()

SELECT SUSER_NAME(1)
SELECT SUSER_NAME(2)
SELECT SUSER_NAME(3)
SELECT SUSER_NAME(4)
SELECT SUSER_NAME(5)
```



