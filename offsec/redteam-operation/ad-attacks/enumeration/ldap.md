# ldap

## ldapsearch

```csharp
ldapsearch -h 10.110.0.222 -x -s base namingcontexts
```

![](../../../../.gitbook/assets/image%20%2892%29.png)

### Retrieve everything

```csharp
ldapsearch -h 10.110.0.222 -D 'Crook\homer_potter' -x -W -b "DC=crook,DC=badcorp,DC=local"
```

### Objects queries

`(ObjectClass=<INPUT HERE>)`

```csharp
ldapsearch -h 10.110.0.222 -D 'Crook\homer_potter' -x -W -b "DC=crook,DC=badcorp,DC=local" '(ObjectClass=person)' | grep name 
```

![](../../../../.gitbook/assets/image%20%2868%29.png)

