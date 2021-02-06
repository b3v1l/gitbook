# i3-plasma

## i3-plasma

```csharp
pacman -S xorg plasma plasma-wayland-session kde-applications 
systemctl enable sddm.service
```

### xsession

```csharp
cat /usr/share/xsessions/plasma.desktop

[Desktop Entry]
Type=XSession
Exec=env KDEWM=/usr/bin/i3 /usr/bin/startplasma-x11
DesktopNames=KDE
Name=Plasma (i3)
Comment=Plasma by KDE w i3

```

### .xinitrc

```csharp
#!/bin/sh

exec /usr/bin/i3
xset +fp $HOME/.local/share/fonts
xset fp rehash

```



### Launch i3 before plasma

```csharp
cat .config/plasma-workspace/env/wm.sh

#!/bin/sh
export KDEWM=/usr/bin/i3
```

### Resources

{% embed url="https://userbase.kde.org/Tutorials/Using\_Other\_Window\_Managers\_with\_Plasma\#Using\_Another\_Window\_Manager\_with\_Plasma" %}





