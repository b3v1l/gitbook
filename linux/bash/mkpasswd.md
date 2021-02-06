# mkpasswd

## mkpasswd

### creating password hashes suitable for /etc/shadow

```csharp
// with a choosen salt
mkpasswd -m sha-512 password -s "11223344"
```

