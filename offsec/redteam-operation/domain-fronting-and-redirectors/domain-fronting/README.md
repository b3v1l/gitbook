# Domain Fronting

## Domain Fronting

Payloads appear to beacon to popular domain and leverage SSL certificates of the CDN.

![](../../../../.gitbook/assets/image%20%28107%29.png)

#### Domain fronting request example :

```csharp
curl -H “host: your-cdn-address.azureedge.net” http://ajax.microsoft.com/?q=thisisatestparameter
```

