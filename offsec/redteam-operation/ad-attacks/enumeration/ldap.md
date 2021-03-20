# ldap

## ldapsearch

```csharp
ldapsearch -h 10.110.0.222 -x -s base namingcontexts
```

![](../../../../.gitbook/assets/image%20%28143%29.png)

### Retrieve everything

{% hint style="info" %}
Authentication is maybe require.

**-D Username**

**-W Password prompt**
{% endhint %}

```csharp
ldapsearch -h 10.110.0.222 -D 'Crook\homer_potter' -x -W -b "DC=crook,DC=badcorp,DC=local"
```

![](../../../../.gitbook/assets/image%20%28149%29.png)

### Objects queries

`(ObjectClass=<INPUT HERE>) <FIELD> <FIELD>`

```csharp
ldapsearch -h 10.110.0.222 -D 'Crook\homer_potter' -x -W -b "DC=crook,DC=badcorp,DC=local" '(ObjectClass=person)' sAMAccountName distinguishedName
```

![](../../../../.gitbook/assets/image%20%2898%29.png)

