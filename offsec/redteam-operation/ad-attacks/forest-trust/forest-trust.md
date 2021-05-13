# Forest Enumeration

## Forest Enumeration

### nltest utils

```csharp
 nltest /trusted_domains
```

![](../../../../.gitbook/assets/image%20%28301%29.png)

### Powershell

```csharp
([System.DirectoryServices.ActiveDirectory.Domain]::GetCurrentDomain()).GetAllTrustRelationships()
```

![](../../../../.gitbook/assets/image%20%2834%29.png)

### Powerview

```csharp
Get-DomainTrust -API
```

![](../../../../.gitbook/assets/image%20%28239%29.png)







