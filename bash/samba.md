# Samba

## Samba

### list user

```csharp
 sudo pdbedit -L -v
```

### Add user

```csharp
sudo smbpasswd -a username
```

## Smbclient

### recursive download

```csharp
smbclient '\\server\share'
    mask ""
    recurse ON
    prompt OFF
    cd 'path\to\remote\dir'
    lcd '~/path/to/download/to/'
    mget *
```

### Upload file

```csharp
smbclient -U DOMAIN/user \\\\10.4.5.17\\c$ --directory temp -c 'put output.txt'
```

### Get server/share info

```text
smbclient -L //172.16.7.131 -I
```

## Samba

### Add owner

`getfacls` `setfacls`

