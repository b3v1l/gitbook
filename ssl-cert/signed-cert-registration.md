# Signed Cert registration

## Signed Cert registration

### Ubuntu install

```text
add-apt-repository ppa:certbot/certbot
apt update && apt install python-certbot-apache

```

### Setup SSL 

```text
certbot --apache --register-unsafely-without-email -d MY_DOAMIN.com
```

![](../.gitbook/assets/image%20%28279%29.png)

Test your cert

{% embed url="https://www.ssllabs.com/ssltest/analyze.html?d=" %}

