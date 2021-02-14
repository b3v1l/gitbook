# Powershell

## Enumeration

### Language Restriction

```text
$ExecutionContext.SessionState.LanguageMode
```

### Is 64bit Operating System

```text
[environment]::Is64BitOperatingsystem 
```

### Is 64bit process

```csharp
[environment]::Is64BitProcess 
```

### User SID

```csharp
 $env:computername
 [wmi] "Win32_userAccount.Domain='ELCHAMAN',Name='Administrator'"
```

![](../../../../.gitbook/assets/image%20%28238%29.png)



