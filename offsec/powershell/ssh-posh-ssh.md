# SSH/SCP \(POSH-SSH\)

## SSH \(POSH-SSH\)

### Install the module

```csharp
install-module -Name Posh-SSH
```

### Set remote credentials

```csharp
$creds = Get-Credential
```

![](../../.gitbook/assets/image%20%2876%29.png)

### Connect

```csharp
 New-SSHSession -ComputerName "REMOTE_TARGET" -Credential $creds
```

### List sessions

```csharp
Get-SSHSession | fl
```

### Execute remote commands

```csharp
Invoke-SSHCommand -Index 0 -Command "uname -a"
```

### Upload files

```csharp
 Set-SCPFile -LocalFile .\Downloads\MY_FILE.TXT -RemoteFile "/tmp/MY_FILE.txt" -ComputerName "Target_COMPUTER" -Credential  $creds
```

### Download Files

```csharp
Get-SCPFile -LocalFile .\Downloads\MY_FILE.TXT -RemoteFile "/tmp/MY_FILE.txt" -ComputerName "Target_COMPUTER" -Credential  $creds
```

### Disconnect session

```csharp
Remove-SSHSession -Index 0 -Verbose
```

## SFTP \(same module\)

### Install the module

```csharp
install-module -Name Posh-SSH
```

### Set remote credentials

```csharp
$creds = Get-Credential
```

### Create Session

```csharp
New-SFTPSession  -ComputerName "Target_COMPUTER" -Credential  $creds -Verbose | fl
```

### List session

```csharp
Get-SFTPSession  | fl
```

### Update PATH

```csharp
PS C:> Get-SFTPCurrentDirectory -Index 0 /root
PS C:> Set-SFTPDirectoryPath -Index 0 -Path /usr/bin
PS C:> Get-SFTPCurrentDirectory -Index 0 /usr/bin
```

### L:ist Folders

```csharp
PS C:\> Get-SFTPDirectoryList -Index 0 -Path /tmp
```

### Download - Upload - Move - Delete Files

```csharp
Get-SFTPFile – Download a specified file from a remote SFTP session.
Move-SFTPFile – Moves a specified file in a remote hosts through SFTP (Can be used to rename a file)
Remove-SFTPFile – Deletes a specified file in a remote hosts through SFTP.
Set-SFTPFile – Uploads a specified file to a given path using SFTP.
```

