# Metasploit/proxychains

## Metasploit

{% hint style="info" %}
From a owned box located on a non routable network
{% endhint %}

### Autoroute

#### Will add the internal route accessible from the owned session

```text
use multi/manage/autoroute
set session X
exploit 

```

```text
use auxiliary/server/socks4a
set srvhost 127.0.0.1
exploit -j
```

Then configure proxychains

![](../../.gitbook/assets/image%20%2844%29.png)





