# SPN

## Registration

```csharp
setspn.exe -A  "MSSQLSvc/sqlprod.crook.badcorp.local:1433" "CROOK\sqladmin"
```

## Deletion

```csharp
setspn.exe -D  "MSSQLSvc/sqlprod.crook.badcorp.local:1433" "CROOK\sqladmin"
```

