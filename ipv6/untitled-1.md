# Disable IPV6 on Linux

## Disable IPV6 on Linux \(permanent\)

### Permanent

* Edit `/etc/sysctl.conf` and add 

```text
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

* Edit `/etc/default/grub` and add

```text
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash ipv6.disable=1 "
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```

* Rebuild grub 

```text
update-grub
```

### Disable for the session

```text
sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
sudo sysctl -w net.ipv6.conf.lo.disable_ipv6=1
```

