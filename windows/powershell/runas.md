# runas

## runas

### Create credentials

```csharp
$username = 'b3v1l'
$password = 'Password123'
$securePassword = ConvertTo-SecureString $password -AsPlainText -Force
$credential = New-Object System.Management.Automation.PSCredential $username, $securePassword
```

### Start a process

```csharp
Start-Process C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe "/U psh.exe" -Credential $credential
```

