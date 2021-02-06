# Windows Defender

## Windows Defender

Require high privilege account

### Disable AV

```csharp
PS C:\Users\b3v1l\Desktop> Set-MpPreference -DisableBehaviorMonitoring $true
PS C:\Users\b3v1l\Desktop> Set-MpPreference -DisableRealtimeMonitoring $true
PS C:\Users\b3v1l\Desktop> Set-MpPreference -SubmitSamplesConsent NeverSend
PS C:\Users\b3v1l\Desktop> Set-MpPreference -MAPSReporting Disabled
```

### Create Exclusion folder

```csharp
PS C:\> Add-MpPreference -ExclusionPath C:\Users\b3v1l\Desktop\tools\
```



