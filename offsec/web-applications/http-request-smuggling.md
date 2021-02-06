# HTTP request smuggling

## HTTP request smuggling

effective way to detect HTTP request smuggling vulnerabilities is to send requests that will cause a time delay in the application's responses if a vulnerability is present.

Content-Lenght and Transfer Encoding

```text
CL.TE Vulnerability 

1
A

X

TE.CL

0

X
```

## HTTP Smuggling

![](../../.gitbook/assets/000387a14c3a4b5c9c6a45922c881820.png)

### CL.TE Desync attack

![](../../.gitbook/assets/5a73f61c00104cb0ab8dc8078de87a36.png)

![](../../.gitbook/assets/9a08305b04bf45128509204a9c0bc62b.png)

![](../../.gitbook/assets/3248d6ba99774eea926e29b5fbb80c49.png)

### TE.CL Desync attack

![](../../.gitbook/assets/014a709ba4ce4a11b672df58837b724b.png)

![](../../.gitbook/assets/51acc5e154b844d9bc4548fa79eed92c.png)

-&gt; post to a place where the attacker have access.

![](../../.gitbook/assets/1a97484b7b034bd4a0c4d6f25f9732a9.png)

#### Payload

![](../../.gitbook/assets/5aa9391fe0f141cca9af70b7073ee344.png)

![](../../.gitbook/assets/ce1797f145eb43bdaf52c625de8a46fa.png)

### CL.TE -&gt; open Desync

![](../../.gitbook/assets/ea2f47c98be841a783f312d039691e28.png)

![](../../.gitbook/assets/07184287326d45859797a93fe2f78440.png)

![](../../.gitbook/assets/e0498c15250d447daf3ae0c7491aabbd.png)

#### Payload

![](../../.gitbook/assets/2124f77adcd9476fae56dc41f7bb7aa7.png)

![](../../.gitbook/assets/42136fb45b8941d2a00de6b467f4c57e.png)

### GraphQL targets

![](../../.gitbook/assets/920aee8706c64db2a0652a07846aa061.png)

### CL.TE -&gt; Open Desync

![](../../.gitbook/assets/d4e342786eaf479bbd8180900df786f7.png)

#### Payload

![](../../.gitbook/assets/63a69114424d4bd9a9de4f1098fb3cfc.png)

* Content lenght must be set to a long value

![](../../.gitbook/assets/4bc484b86e3c44049d8b880ed0f64f0e.png)

### POC

![](../../.gitbook/assets/10f8ce3d08e14c64ae2ebfe02b061578.png)

![](../../.gitbook/assets/8b9802f420c14e4a8caf49f2bb8de43e.png)

![](../../.gitbook/assets/20285a0b88514eb7a7b69f7ae1fcd8b0.png)

![](../../.gitbook/assets/5f031382272242588411e3287cbbac99.png)

![](../../.gitbook/assets/7388b9ff5bdf432bb8590225560c6345.png)

pipedream

### POC2

Session stealing using Response Queue 

![](../../.gitbook/assets/2b8c6b89d3794f14884d122909c1d480.png)



![](../../.gitbook/assets/11dd54f921b443b6b8ebd1efaed04557.png)

### Resources

All credit goes to @defparm

{% embed url="https://github.com/defparam/smuggler" %}

#### Turbo intruder scripts.

{% embed url="https://github.com/defparam/tiscripts" %}





​​

















