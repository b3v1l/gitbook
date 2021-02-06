# find

## find

### **Execute**

```csharp
find . -type f -exec chmod 660 {} \; 
find . -type f -exec chmod 660 {} \; find . -type d -execdir chmod 660 {} +
```

### Find a computer + login fron log

`zcat computer.*gz | grep -B 2 -A 2 user | grep succeeded | grep -v gka`

`zcat named.log.10.gz named.log.9.gz named.log.8.gz named.log.7.gz named.log.6.gz named.log.5 named.log.4.gz named.log.3.gz named.log.2.gz named.log.1.gz | cat - named.log | egrep '`_`torrent`_`' | awk '{print $1,$2,$3,$11,$13}' > /tmp/test.txt`

`for i in ls ; do echo "$i"; cat $i |grep Download | awk '{ SUM += $2} END { print SUM/221}'; cat $i |grep Upload | awk '{ SUM += $2} END { print SUM/221}'; done > test.txt`

### **Find suid bit**

```csharp
 find / -perm -u=s -exec ls -al {} +
```

```csharp
find / -perm -g=s -o -perm -4000 ! -type l -maxdepth 3 -exec ls -ld {} \; 2>/dev/null
find / -perm -u=s -type f 2>/dev/null find / -perm -g=s -type f 2>/dev/null
```

### **files modified between 2 dates** 

```csharp
find / -type f -newermt 2018-02-20 ! -newermt 2018-02-25 -ls 2>/dev/null
```

