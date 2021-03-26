# Own password list

## Password list

### Create a file

![](../../../../.gitbook/assets/image%20%28171%29.png)

#### Add date

```csharp
for i in $(cat password.lst); do echo $i; echo ${i}2020 ; echo ${i}2021; done
```

#### Add exclamation mark

```csharp
for i in $(cat password.lst); do echo $i; echo ${i}\!; done > temp 
```

### Hashcat rules

```csharp
hashcat --force --stdout password.lst -r /usr/share/doc/hashcat/rules/best64.rule > temp 
```

#### Combined rules + length limit

```csharp
hashcat --force --stdout password.lst -r /usr/share/doc/hashcat/rules/best64.rule -r /usr/share/doc/hashcat/rules/toggles1.rule | sort -u | awk 'length($0) > 8'  
```

