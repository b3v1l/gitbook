# Domain Fronting

## Domain Fronting

Payloads appear to beacon to popular domain and leverage SSL certificates of the CDN.

![](<../../../../.gitbook/assets/image (107) (1).png>)

#### Domain fronting request example :

```csharp
curl -H “host: your-cdn-address.azureedge.net” http://ajax.microsoft.com/?q=thisisatestparameter
```
