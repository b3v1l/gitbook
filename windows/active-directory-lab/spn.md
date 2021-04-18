# SPN

## Registration

```csharp
setspn.exe -A  "MSSQLSvc/sqlprod.crook.badcorp.local:1433" "CROOK\sqladmin"
```

## Deletion

```text
setspn.exe -D  "MSSQLSvc/sqlprod.crook.badcorp.local:1433" "CROOK\sqladmin"
```

