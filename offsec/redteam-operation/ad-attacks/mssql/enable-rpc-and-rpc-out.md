# Enable RPC and RPC out

## Enable RCP and RCP out

{% hint style="info" %}
sysadmin privilege requires on the initial server
{% endhint %}

```csharp
select * from master..sysservers;
EXEC sp_serveroption 'SQLDEV', 'rpc', 'true'; 
EXEC sp_serveroption 'SQLDEV', 'rpc out', 'true';
select * from master..sysservers ;
```



