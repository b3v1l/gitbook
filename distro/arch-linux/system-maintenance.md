# System Maintenance

## System Maintenance

### Systemctl

#### Failed services 

```csharp
systemctl --failed
```

#### Logs files

```csharp
sudo journalctl -p 3 -xb
```

### Updates

```csharp
pacman -Syu
yay -Syu
```

### Cache Cleaning

#### Remove uninstalled packages stored in cache

```csharp
pacman -Sc
yay -Sc
```

#### Remove everything from the cache \(caution\)

```csharp
pacman -Scc
yay -Scc
```

#### Remove unwanted dependencies with yay

```csharp
yay -Yc
```

### Clean journal logs

```csharp
journalctl --verify
# Clean journal entries using date value (clean everything before 2 weeks)
journalctl --vaccuum-time=2weeks
```

### Orphaned packages

* List the orphaned packages

```csharp
pacman -Qtdq
```

* Remove them

```csharp
sudo pacman -Rns $(pacman -Qtdq)
```

### Mirros

#### Install reflector 

```csharp
sudo pacman -Sy community/reflector
```

#### Find fastest and updated mirrors and save them in mirrorlist

```csharp
sudo reflector -c Belgium -a 6 --sort rate --save /etc/pacman.d/mirrorlist
```

