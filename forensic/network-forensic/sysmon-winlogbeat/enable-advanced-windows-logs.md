# Enable advanced Windows Logs

## Enable advanced Windows Logs

* mmc.exe
* Crtl + m
* Add Group Policy

### Enable Command line logging

* Audit Process Creation

![](../../../.gitbook/assets/1b57cb04c8ad4be79d6b483b99c20d96.png)

* Enable it

![](../../../.gitbook/assets/5bc45989245240a18573818ac1a4dc90.png)

* Audit Force audit policy

![](../../../.gitbook/assets/c510f16a67714d2eb5a91b40eebfc261.png)

* Details tracking



* Admin template Audit Process Creation

![](../../../.gitbook/assets/091f88ae5ef74de0a3859c95c90fa778.png)

### Powershell Logging

* Check for window powershell

![](../../../.gitbook/assets/b196067061f34da0a6ec983785f28372.png)

![](../../../.gitbook/assets/f7c7813f519f40b88da3c791d6eed2ca.png)

* Also add Script Block Logging

![](../../../.gitbook/assets/6bbbc8eb3a044df2806bc43a5fbed860.png)

* Create a powershell profil.ps1

![](../../../.gitbook/assets/eea814582a6342619e1c4213274088bb%20%281%29.png)

```csharp
$LogCommandHealthEvent = $True
$LogCommandLifecycleEvent = $True
```

* copy it in windows powershell folder

![](../../../.gitbook/assets/0796f826327d4ccc8bb80e289ebd863c.png)



### Enable Task Scheduled logging

![](../../../.gitbook/assets/0aa9644ef1d7473290cce86ce1bc2b02.png)

