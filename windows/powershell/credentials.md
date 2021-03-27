# Share and Credentials

## Create credentials

```csharp
$pass = convertto-securestring 'MyPAssword' -AsPlainText -Force
$creds = New-Object System.Management.Automation.PSCredential('polo',$pass)
```

![](../../.gitbook/assets/image%20%28188%29.png)

## Mount the share

```csharp
New-PsDrive -Name Test -PSProvider FileSystem -Credential $cred -Root \\10.110.0.66\Test
```



