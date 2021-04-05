# Linked DB

## Linked DB

Add a linked server to a controlled MSSQL server

```csharp
USE [master]  ;
EXEC master.dbo.sp_addlinkedserver   
    @server = N'SQLDEV',   
    @srvproduct=N'SQL Server' ;  

```

Add current account

```csharp
EXEC master.dbo.sp_addlinkedsrvlogin   
    @rmtsrvname = N'SQLDEV',   
    @locallogin = NULL ,   
    @useself = N'True' ;   
```

