# openssl

## openssl

### self-signed certificate and private key

```csharp
openssl req -new -x509 -nodes -out cert.crt -keyout priv.key
```

### PEM cert

```csharp
cat priv.key cert.crt > nasa.pem
```

### change the CipherString

Edit `/etc/ssl/openssl.cnf` and change the following line 

```csharp
CipherString=DEFAULT@SECLEVEL=2

To

CipherString=DEFAULT
```



