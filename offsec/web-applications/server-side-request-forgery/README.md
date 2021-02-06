# Server Side Request Forgery

## SSRF Example

* in a web application, the user can set a link to an external website to set his picture profil ...

  The server make a request on the remote site to get the picture .

#### SSRF enables you to

```text
• Access service which are listened on loopback only
• Scan the internal network and potentially interact with those services (using get/post/head)
• Read local file using file://
• Move laterally into the internal environment
```

