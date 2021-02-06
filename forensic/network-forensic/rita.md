# Rita

## Rita

### Test config

```csharp
rita test-config | less
```

### List DB and logs

```csharp
rita list
```

![](../../.gitbook/assets/image%20%28175%29.png)

### Importing logs from Bro/Zeek

```csharp
rita import --rolling /opt/bro/logs/$(date --date='-1 hour' +%Y-%m-%d)/ dataset_name
```

### show datababe

```csharp
rita show-databases
```

### show long connections

```csharp
rita show-long-connections dataset_name
sudo rita show-long-connections dataset_name | cut -d , -f 1,2,4 |datamash -H -t , -g 1,2 sum 3 | sort -t , -k 3 -rn
```

### show beacons

```csharp
sudo rita show-beacons dataset_name | head
```

### Exposed DNS

```csharp
sudo rita show-exploded-dns dataset_name | head
```

### Add an exclude list

```csharp
rita show-beacons DB_NAME | grep -v -w -F -f exclude.txt
```

### Resources

{% embed url="https://www.blackhillsinfosec.com/projects/rita/" %}

