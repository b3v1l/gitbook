# PowerUpSQL

## Enumeration

```csharp
Get-SQLInstanceDomain | Get-SQLConnectionTestThreaded -Verbose
Get-SQLInstanceDomain | Get-SQLServerInfo -Verbose
```

#### Default login

```csharp
 Get-SQLServerLoginDefaultPw -Verbose -Instance <SERVER>
```

### Dump

```csharp
Invoke-SQLDumpInfo -Verbose -Instance <SERVER>
```

