# Windows Defender

## Windows Defender

Require high privilege account

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



