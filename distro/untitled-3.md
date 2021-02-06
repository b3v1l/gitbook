# Debian

## Debian  <a id="downgrade-package"></a>

### Downgrade package

```text
aptitude install samba=2:3.6.6-6+deb7u7
```

### Check different package version installed and available :

```text
apt-cache policy firefox
apt install firefox=45.0.2+build_blablabla
```

### Clean disk \(make space\)

```aspnet
 // Remove stored package from disk
 apt-get clean
 
 // Clean temps thumbnails
 rm -rf ~/.cache/thumbnails/*
 
 // Check and delete logs size
 journalctl --disk-usage
Archived and active journals take up 3.9G in the file system.

//delete number of days
sudo journalctl --vacuum-time=1d
```

### Disable Ipv6 for apt

```csharp
sudo vim /etc/apt/apt.conf.d/99force-ipv4

Add this line :
Acquire::ForceIPv4 “true”;


```

