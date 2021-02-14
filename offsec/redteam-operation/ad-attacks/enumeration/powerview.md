# Powerview

## Domain

{% hint style="warning" %}
All of these commands must be used in the context of an already joined domain machine.
{% endhint %}

### Domain Info

```csharp
Get-NetDomain
Get-NetDomain -Domain crook.badcorp.local
```

![](../../../../.gitbook/assets/image%20%2877%29.png)

### Domain Controller

```csharp
Get-NetDomainController
```

### Domain Policies

```csharp
Get-DomainPolicy
(Get-DomainPolicy)."system access"
```

![](../../../../.gitbook/assets/image%20%28288%29.png)

### Domain Trust

```csharp
Get-NetDomainTrust
```

![](../../../../.gitbook/assets/image%20%2849%29%20%281%29.png)

```csharp
Get-NetForestDomain
```

![](../../../../.gitbook/assets/image%20%28115%29.png)

```text
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

![](../../../../.gitbook/assets/image%20%28174%29.png)

```csharp
Get-NetUser -UserName REX_ARMSTRONG
```

![](../../../../.gitbook/assets/image%20%28129%29%20%281%29.png)

### Users Proprieties

```csharp
Get-UserProperty -Properties pwdlastset
```

![](../../../../.gitbook/assets/image%20%284%29.png)

### Users Fields

```csharp
Find-UserField -SearchField Description -SearchTerm "*built*"
```

![](../../../../.gitbook/assets/image%20%28169%29.png)

### Logged user

{% hint style="warning" %}
Need admin privileges on the target
{% endhint %}

```csharp
 Get-NetLoggedon -ComputerName helpdesk
```

![](../../../../.gitbook/assets/image%20%2863%29.png)

## Foreign users

```csharp
Get-DomainForeignGroupMember -Verbose -Domain domain.com
Get-ADObject -Domain domain.com   | ?{$_.objectsid -eq 'S-1-5-21-<SID Object>'}
```

## Groups

### Groups info

```csharp
Get-NetGroup -Domain crook.badcorp.local
```

![](../../../../.gitbook/assets/image%20%28109%29.png)

```csharp
Get-NetGroup  "*Admin*"
Get-NetGroup  "DnsAdmins"  -FullData
```

![](../../../../.gitbook/assets/image%20%2817%29.png)

```csharp
Get-NetGroup -domain moneycorp.local -GroupName "Domain Admins" -FullData
Get-Nt-NetGroupMember -Domain crook.badcorp.local -GroupName "Enterprise Admins"
```

#### Recursive groups 

```csharp
Get-NetGroupMember -GroupName "Administrators" -Recurse
```

![](../../../../.gitbook/assets/image%20%28127%29.png)

## Domain Computers

### Domain computers info

```csharp
Get-NetComputer -FullData | more
```

![](../../../../.gitbook/assets/image%20%28186%29.png)

```csharp
Get-NetComputer -OperatingSystem "*Server*"
```

![](../../../../.gitbook/assets/image%20%2875%29.png)

## ACE 

{% hint style="info" %}
DACL = Discretionary Access ControlList  
DACL composed of a serie of Access Control Entries \(ACE\)  
ACE are stored into a SecurityDescriptor Definition Language \(SDDL\)  
  
- SDDL prototype  
  
**ace\_type;ace\_flags;rights;object\_guid;inherit\_object\_guid;account\_sid**  
  
Ex:  
  
**\(A;;RPWPCCDCLCSWRCWDWOGA;;;S-1-1-0\)**  
  
AceType:  
**A = ACCESS\_ALLOWED\_ACE\_TYPE**  
  
**Access rights:  
RP = ADS\_RIGHT\_DS\_READ\_PROP  
WP = ADS\_RIGHT\_DS\_WRITE\_PROP  
CC = ADS\_RIGHT\_DS\_CREATE\_CHILD  
DC = ADS\_RIGHT\_DS\_DELETE\_CHILD  
LC = ADS\_RIGHT\_ACTRL\_DS\_LIST  
SW = ADS\_RIGHT\_DS\_SELF  
RC = READ\_CONTROL  
WD = WRITE\_DAC  
WO = WRITE\_OWNER  
GA = GENERIC\_ALL  
  
Ace Sid:S-1-1-0**
{% endhint %}

### Powerview and related right 

![](../../../../.gitbook/assets/image%20%28136%29.png)

### ACE Enumeration 

### Filter by user

{% hint style="warning" %}
The following command can be used on a specific child domain\(...\) and can be used to quickly filter specific field : 

```text
 select Identity, ObjectDN,ActiveDirectoryRights | ft
```
{% endhint %}

```text
Get-DomainUser -domain ops.comply.com | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} |  Where-Object {$_.ActiveDirectoryRights -like "*Generic*" } | select Identity, ObjectDN,ActiveDirectoryRights | ft
```

```csharp
Get-ObjectAcl -Identity ted -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_}
Get-ObjectAcl -Identity user -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_}
```

```csharp
Get-DomainUser | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_} | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} | Foreach-Object {if ($_.Identity -eq $("$env:UserDomain\$env:Username")) {$_}}
```

### GenericAll 

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
Add-DomainObjectAcl -TargetIdentity OwnedService -PrincipalIdentity myuser -Rights All
```

### GenericWrite

```csharp
Get-DomainUser | Get-ObjectAcl -ResolveGUIDs | Foreach-Object {$_ | Add-Member -NotePropertyName Identity -NotePropertyValue (ConvertFrom-SID $_.SecurityIdentifier.value) -Force; $_} |  Where-Object {$_.ActiveDirectoryRights -like "*GenericWrite*" }
```

#### Set up a ServicePrincipal name on the target account 

```csharp
Set-DomainObject -Identity ownedservice -SET @{serviceprincipalname='nonexistent/BLAHBLAH'}
$User = Get-DomainUser iwnedservice
$User | Get-DomainSPNTicket | fl
```

![](../../../../.gitbook/assets/image%20%2810%29.png)

```

```

![](../../../../.gitbook/assets/image%20%28274%29.png)

## Shares

### Find shares

```csharp
Invoke-ShareFinder -Verbose -ExcludeStandard -ExcludePrint -ExcludeIPC
```

![](../../../../.gitbook/assets/image%20%2833%29.png)

## GPO

### GPO enum

```csharp
Get-NetGPO | select displayname
# Restricted groups
Get-NetGPOGroup -Verbose

Get-NetGPO -ComputerName <server>
```

#### Classic gpresult

```text
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

![](../../../../.gitbook/assets/image%20%2883%29.png)

```csharp
Get-NetGPO -GPOname '{6AC1786C-016F-11D2-945F-00C04fB984F9}'
```

#### Get items from OU

```csharp
Get-NetOU *test* | %{Get-NetComputer -ADSPATH $_}
```

## Resources

{% embed url="https://github.com/PowerShellMafia/PowerSploit" %}

