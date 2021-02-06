# ssd

## ssd

* Config file

```csharp
cat /usr/lib/systemd/system/fstrim.service

[Unit]
Description=Discard unused blocks on filesystems from /etc/fstab
Documentation=man:fstrim(8)
ConditionVirtualization=!container

[Service]
Type=oneshot
ExecStart=/usr/bin/fstrim --listed-in /etc/fstab:/proc/self/mountinfo --verbose --quiet-unsupported
PrivateDevices=no
PrivateNetwork=yes
PrivateUsers=no
ProtectKernelTunables=yes
ProtectKernelModules=yes
ProtectControlGroups=yes
MemoryDenyWriteExecute=yes
SystemCallFilter=@default @file-system @basic-io @system-service

```

### Trim

* List timers

```csharp
systemctl list-timers
```

* Enable trim

```csharp
systemctl enable --now fstrim.timer
systemctl start fstrim.service
```

*  Get logs

```csharp
journalctl -b -u fstrim.service
```



