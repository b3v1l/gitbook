# Domain SID

## Get Domain SID

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

