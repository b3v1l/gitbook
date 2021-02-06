# HTA

## HTA

### About

HTA = html Application

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



