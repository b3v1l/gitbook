# Linux Hardening

## Linux Hardening

### Check Modules signature

```csharp
for i in $(lsmod | tail -n +2 | cut -d ' ' -f1);do modinfo ${i} | grep -q "signature" || echo "no signatures for module: ${i}" ; done
```

### Check secure boot

```csharp
sudo mokutil --sb-state
```

### fail2ban



2

### Basic firewall rules \(ufw\)

```csharp
sudo ufw limit 22/tcp                                                                                                                                                                   
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw enable                
```



