# Windows Remote Shell \(WinRM\)

## WinRM

### Enable the service

```csharp
WinRM quickconfig
start-service winrm
```

### Open a session

```csharp
$f = new-pssession -computer <Computer>
etsn $f
```

### Execute a command

```csharp
invoke-command -ScriptBlock{ipconfig} $f
```

### Kerberos Double Hop

```csharp
$f = new-pssession -computer <Computer>
etsn $f
# On remote host
$next = new-pssession -computer <Computer>

invoke-command -ScriptBlock{invoke-command -ScriptBlock{hostname}$next } $f
```

### Load a script

```csharp
invoke-command -FilePath c:\myscript.ps1 $f
```

