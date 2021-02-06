# Proxy

## Proxy

### Get Proxy info

```csharp
[System.Net.WebRequest]::DefaultWebProxy.GetProxy("http://192.168.x.x/file")
```

### bypass Proxy settings

```csharp
$wclient = New-Object System.Net.WebClient
$wclient.proxy = $null
$wclient.DownloadString("http://example.com")
```

### Custom User agent

```csharp
$w = new-object system.net.WebClient
$w.Headers.Add('User-Agent', "Mozilla/5.0 (Linux; Android 4.0.3; KFTT) AppleWebKit/537.36 (KHTML, like Gecko) Silk/73.7.5 like Chrome/73.0.3683.90 Safari/537.36")
```



