# VBA macros - DotNetToJScript

## VBA macros - DotNetToJScript

### About

DotNetToJScript can alos be used to generate VBA code -&gt; office Macro.

From there, we can create a malicious C\# code using the Queue

### Create the C\# code

* Remove `static` from main method
* Create 2 base64 encoded shellcode
* Note Class name used

![](../../../../.gitbook/assets/image%20%28236%29.png)

### Compile the DLL

* use csc.exe using .Net Framework version 2 

```csharp
 C:\Windows\Microsoft.NET\Framework\v2.0.50727\csc.exe /target:library .\queueVBA_test.cs
```

![](../../../../.gitbook/assets/image%20%2842%29.png)

### DotNetToJScript VBA

* Use .Net version 2 `-v v2`

```csharp
.\DotNetToJScript.exe -v v2 -l VBA -c QueueTest -o C:\Users\b3v1l\Documents\code\c#\VBA-DotnetToJS\vba_output.txt C:\Users\b3v1l\Documents\code\c#\VBA-DotnetToJS\queueVBA_test.cs
```

![](../../../../.gitbook/assets/image%20%2871%29.png)

### Weaponize Office document

* go to Dev Tools -&gt; Virtual Basic and copy the DotNetToJScript VBA output into "This Document".

![](../../../../.gitbook/assets/image%20%28211%29.png)

* Add the C\# method name at the end of the Run function and Add Sub function to allow the macro to run when the document is opened.

![](../../../../.gitbook/assets/image%20%28284%29.png)

* Save the file \(as macro enabled document docm\)

![](../../../../.gitbook/assets/image%20%2862%29.png)

![](../../../../.gitbook/assets/image%20%2857%29.png)

* Remote template injection can also be used to hide a little more what we want to achieve here.



