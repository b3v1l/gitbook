# SSL Certificat

## SSL Certificat

### Create a certificat

```csharp
 openssl req -new -x509 -nodes -out cert.crt -keyout priv.key
 cat priv.key cert.crt > nsa.pem
```





Add a custom SSL cert on the listener

```csharp
 set HandlerSSLCert /path/to/the/cert.pem
```

