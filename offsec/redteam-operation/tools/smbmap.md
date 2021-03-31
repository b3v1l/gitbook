# smbmap

## Shares enumeration

### Unauthenticated

```csharp
smbmap -H 10.110.0.222
```

### Authenticated

#### Password

```csharp
smbmap -u jsmith -p password1 -d workgroup -H 192.168.0.1
```

#### NTLM Hash

```csharp
-u jsmith -p 'aad3b435b51404eeaad3b435b51404ee:da76f2c4c96028b7a6111aef4a50a94d' -H 172.16.0.20
```

#### Domain authentication

```csharp
smbmap -u 'apadmin' -p 'asdf1234!' -d ACME -Hh 10.1.3.30 -x 'net group "Domain Admins" /domain'
```

### List contents of directory

```csharp
smbmap -r <FOLDER> -H 10.110.0.222 -A <Search Pattern> -q
```



