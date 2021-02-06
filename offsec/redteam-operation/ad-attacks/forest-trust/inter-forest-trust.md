# Inter Forest Trust

## Enumeration

```csharp
 ([System.DirectoryServices.ActiveDirectory.Forest]::GetCurrentForest()).GetAllTrustRelationships()
```

### Powerview

```csharp
Get-ForestTrust
```

```csharp
 Get-DomainTrust -Domain target.com
```

```csharp
Get-DomainTrustMapping
```

## foreign user accounts

search for inter forest accounts :

```text
Get-DomainForeignGroupMember -Domain target.com
```

Then, convert the SID members names

```text
ConvertFrom-SID <MemberName SID>
```

## Other Forests compromise

by default it is not possible to compromise a trusted forest \(forest trust are set as security boundary\)

### SID filtering

#### Enable SID History

```csharp
netdom trust crook.badcorp.local /d:badcorp.local /enablesidhistory:yes
```

![](../../../../.gitbook/assets/image%20%28305%29%20%281%29.png)

{% hint style="warning" %}
Microsoft dictated that any SID with a RID less than 1000 will always be filtered regardless of the SID history setting -&gt; **RID &gt; 1000 are fine.**

**From there, creating a golden ticket can be used with sid history \(with a sids &gt; 1000\).**
{% endhint %}

\*\*\*\*

