# Install pgp key

## Update key

```csharp
pacman -Sy archlinux-keyring
pacman -Syu
```

## Manual install

### Add the key

```csharp
pacman-key --add /path/to/downloaded/public_key.asc
```

### Key check

```csharp
pacman-key --finger <VALUE_HERE>
```

### Sign the key

```csharp
pacman-key --lsign-key <VALUE_HERE>
```



