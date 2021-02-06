# Bypass proxy extension filters

## Bypass proxy extension filters

### Apache configuration

In some case, proxy can be configured to block some type of file extension.

Using apache configuration, it is possible to bypass those kind of filters :

```text
vim /etc/apache2/apache2.conf
```

* Edit the following line and restart the service.

![](../../../../.gitbook/assets/image%20%28253%29.png)

### .htaccess config

* Create/Edit a .htaccess file and adjust permissions

```text
sudo vim /var/www/.htaccess
```

![](../../../../.gitbook/assets/image%20%28232%29.png)

* Bypass :\)

![](../../../../.gitbook/assets/image%20%2890%29.png)

