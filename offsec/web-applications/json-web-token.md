# Json Web Token

## JWT

Multiple signature methods can be used to ensure the integrity of JWT:

```text
    RSA based
    Elliptic curves
    HMAC
    None
```

### None algorithm for signature

![](../../.gitbook/assets/2cf793492d2d475b862433b8322c9ddd.png)

* Decode the token:

![](../../.gitbook/assets/7d230fa7392d4f0ead7cd7d4213754b5.png)

* Add padding

![](../../.gitbook/assets/947bae5f1e484042918f7a3a6fd6a9c0.png)

* Base64 encoding and remove the signature.

![](../../.gitbook/assets/54abd78e0cdc40a0bbf0e410d72034c0.png)

### Bruteforce HS256 signed JWT

* Clone the repo

```csharp
git clone https://github.com/Sjord/jwtcrack
pip install PyJWT # or yay using arch linux
```

* Convert JWT token to john's format 

```csharp
python3 jwt2john <MY_JWT_TOKEN> > JWToutput.txt
john  JWToutput.txt
```

### Resources

{% embed url="https://auth0.com/blog/critical-vulnerabilities-in-json-web-token-libraries/" %}

{% embed url="https://github.com/Sjord/jwtcrack" %}







