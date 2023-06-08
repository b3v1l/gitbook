# Basic usage

## Basic usage

### Assembly

![](<../../../../.gitbook/assets/image (240).png>)

### Commands execution

```
ShellCmd cmd /c net user
```



### Download / Upload files

* **Upload a file**

```
 Upload /filepath:"C:\Users\HOMER_POTTER\test.exe" 
```

![](<../../../../.gitbook/assets/image (208) (1).png>)

* **Download**

![](<../../../../.gitbook/assets/image (266).png>)



### Enumeration

```csharp
Seatbelt -group=all
```

![](<../../../../.gitbook/assets/image (303).png>)

### Keylogger

#### Set time to run, ie `keylogger 20` to make it run for 20 seconds

![](<../../../../.gitbook/assets/image (111).png>)

### Mimikatz

`LogonPasswords`

![](<../../../../.gitbook/assets/image (222).png>)

### Powershell&#x20;

* **import remote modules**

```
PowerShellImport
```

![](<../../../../.gitbook/assets/image (193).png>)

* Execute commands from the imported module:

```
powershell Get-domainUsers
```

![](<../../../../.gitbook/assets/image (64).png>)

### Sharshell commands&#x20;

### ! case sensitive

#### Using Tokens

```
sharpshell using (Tokens t = new Tokens()) {return t.WhoAmI(); }
```

![](<../../../../.gitbook/assets/image (250).png>)

