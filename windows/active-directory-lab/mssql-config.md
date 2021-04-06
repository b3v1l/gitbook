# MSSQL config



```csharp
select * from openquery("SQLDEV",'SELECT SUSER_NAME()');


# Enable RCP and RCP out

select * from master..sysservers
EXEC sp_serveroption 'SQLDEV', 'rpc', 'true';
EXEC sp_serveroption 'SQLDEV', 'rpc out', 'true';

select * from master..sysservers


EXECUTE ('EXEC sp_configure ''show advanced option'', ''1'';reconfigure;')  AT SQLDEV


use msdb; EXECUTE AS USER = 'dbo'; select * from openquery("SQLDEV",'select @@version as version');



# Search sysadmin account :

SELECT name,type_desc,is_disabled, create_date FROM master.sys.server_principals WHERE IS_SRVROLEMEMBER ('sysadmin',name) = 1; ORDER BY name


SELECT name FROM sys.server_principals



# Search Server Roles

SELECT name FROM sys.server_principals WHERE type_desc = 'SERVER_ROLE'

# grant access to DB + impersonate

USE msdb;
GRANT IMPERSONATE ON USER::dbo to [CROOK\Homer_potter];
GRANT CONTROL ON DATABASE::msdb TO [CROOK\Homer_potter];

REVOKE IMPERSONATE ON USER::sa to [CROOK\Homer_potter];


# Remote access

USE master;
REVOKE IMPERSONATE ON LOGIN::sa to [crook\homer_potter];
```

