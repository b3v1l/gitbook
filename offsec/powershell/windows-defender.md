# Windows Defender

## Windows Defender

{% hint style="info" %}
Require high privilege account
{% endhint %}

### Disable AV

```csharp
Set-MpPreference -DisableBehaviorMonitoring $true
Set-MpPreference -DisableRealtimeMonitoring $true
Set-MpPreference -SubmitSamplesConsent NeverSend
Set-MpPreference -MAPSReporting Disabled
```

### Create Exclusion folder

```csharp
PS C:\> Add-MpPreference -ExclusionPath C:\Users\b3v1l\Desktop\tools\
```



