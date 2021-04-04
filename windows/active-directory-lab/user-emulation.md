# User emulation

## User emulation

### White noise script

```bash
PS C:\Windows\system32> $trigger = New-JobTrigger -AtStartup -RandomDelay 00:00:30 
PS C:\Windows\system32> Register-ScheduledJob -Trigger $trigger -FilePath C:\whitenoise.ps1 -Name Surfbuddy
IResources
```

{% embed url="https://github.com/Relkci/ps-whitenoiseweb/blame/master/WhiteNoise.ps1" %}





