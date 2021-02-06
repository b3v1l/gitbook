# Sysmon

## Modular Sysmon

* Clone the repo
* Open Admin powershell prompt

```csharp
git clone https://github.com/olafhartong/sysmon-modular.git
cd sysmon modular
. .\Merge-SysmonXml.ps1
Merge-AllSysmonXml -Path ( Get-ChildItem '[0-9]*\*.xml') -AsString | Out-File sysmonconfig.xml
```

* Install sysmon

```csharp
.\Sysmon64.exe -i .\sysmonconfig.xml
```

### Resources

{% embed url="https://docs.microsoft.com/en-us/sysinternals/downloads/sysmon" %}

{% embed url="https://github.com/olafhartong/sysmon-modular" %}

