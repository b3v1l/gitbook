# Enumeration

## Powerup

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

![](../../../../../.gitbook/assets/image%20%288%29.png)

## LSASS protection

```csharp
Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Control\Lsa -Name "RunAsPPL"
```

![](../../../../../.gitbook/assets/image%20%2832%29.png)

## AppLocker

```csharp
get-childitem HKLM:\SOFTWARE\Policies\Microsoft\Windows\SrpV2\Exe
```

![](../../../../../.gitbook/assets/image%20%286%29.png)

{% hint style="warning" %}
Applocker is not applied on Local System, Local Service or Network Service.
{% endhint %}



