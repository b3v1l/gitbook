# Enumeration

## PowerUp

Powershell script

```csharp
. .\powerup.ps1
invoke-allchecks
```

## HostRecon

```csharp
. .\HostRecon.ps1
invoke-hostrecon
```

#### Check for AV products, LAPS, firewall ...

![](<../../../../.gitbook/assets/image (8) (1).png>)

## LSASS protection

```csharp
Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Control\Lsa -Name "RunAsPPL"
```

![](<../../../../.gitbook/assets/image (32).png>)

## AppLocker

{% hint style="warning" %}
Applocker is not applied on Local System, Local Service or Network Service.
{% endhint %}

```csharp
get-childitem HKLM:\SOFTWARE\Policies\Microsoft\Windows\SrpV2\Exe
```

![](<../../../../.gitbook/assets/image (6) (1).png>)
