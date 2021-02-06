# Trinity usage

## Set up a listener <a id="set-up-a-listener"></a>

http or https

## Set up a stager <a id="set-up-a-stager"></a>

| Name | Description |
| :--- | :--- |
| csharp | Stage via CSharp source file |
| powershell | Stage via a PowerShell script |
| exe | Generates a windows executable stager |
| dll | Generates a windows dll stager |
| wmic | Stage via wmic XSL execution |
| msbuild | Stage via MSBuild XML inline C\# task |

## Modules <a id="modules"></a>

* **boo/ps**

**List process**

Colored process :

| color | details |
| :--- | :--- |
| Red | AV/EDR process |
| Grey | vmtools |

* boo/minidump

Dump lsass using a python API \(not mimikatz\)

