# Powershell

## Enumeration

### Language Restriction

```text
$ExecutionContext.SessionState.LanguageMode
```

### Is 64bit Operating System

```text
[environment]::Is64BitOperatingsystem 
```

### Is 64bit process

```csharp
[environment]::Is64BitProcess 
```

### Search for files extension

```csharp
Get-ChildItem -Path <folder> -Include *.ini* -File -Recurse -ErrorAction SilentlyContinue
```

### User SID

```csharp
 $env:computername
 [wmi] "Win32_userAccount.Domain='ELCHAMAN',Name='Administrator'"
```

![](../../../../.gitbook/assets/image%20%28238%29.png)

### Domain SID

```text
function global:Get-PrimaryDomainSID ()
{
  # Note: this script obtains SID of the primary AD domain for the local computer. It works both
  #       if the local computer is a domain member (DomainRole = 1 or DomainRole = 3)
  #       or if the local computer is a domain controller (DomainRole = 4 or DomainRole = 4).
  #       The code works even under local user account and does not require calling user
  #       to be domain account.

  [string] $domainSID = $null

  [int] $domainRole = gwmi Win32_ComputerSystem | Select -Expand DomainRole
  [bool] $isDomainMember = ($domainRole -ne 0) -and ($domainRole -ne 2)

  if ($isDomainMember) {

    [string] $domain = gwmi Win32_ComputerSystem | Select -Expand Domain
    [string] $krbtgtSID = (New-Object Security.Principal.NTAccount $domain\krbtgt).Translate([Security.Principal.SecurityIdentifier]).Value
    $domainSID = $krbtgtSID.SubString(0, $krbtgtSID.LastIndexOf('-'))
  }

  return $domainSID
}
```

