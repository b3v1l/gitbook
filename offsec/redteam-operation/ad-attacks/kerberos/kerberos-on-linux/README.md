# Kerberos on Linux

## Kerberos on Linux

### Tickets

#### Ccache file creds

```text
env | grep KRB5CCNAME
```

#### Request a TGT

```text
kinit
klist
kvno MSSQLSvc/sqluat.crook.badcorp.local:1433
```

![](../../../../../.gitbook/assets/image%20%28120%29.png)

![](../../../../../.gitbook/assets/image%20%28194%29.png)

### Search for SPN

```csharp
ldapsearch -Y GSSAPI -H ldap://dc02.crook.badcorp.local -D "Administrator@CROOK.BADCORP.LOCAL" -W -b "dc=crook,dc=badcorp,dc=local" "servicePrincipalName=*" servicePrincipalName
```

```text
kvno MSSQLSvc/sqluat.crook.badcorp.local:1433
```

