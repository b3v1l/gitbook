# tshark

## Tshark

### Filters

```text
tshark -r  capture.pcap -T fields -e ip.src -e ip.dst ip.dst==1.1.1.1 | head
```

### Suspicious DNS traffic in pcap

```csharp
tshark -r capture.pcapng -T fields -e dns.qry.name | sort | uniq | rev | cut -d . -f 1-2 | rev |sort | uniq -c | sort -rn | head -10
```

### IPV4 traffic 

#### ip source + ip destination and count 

```csharp
tshark -r file.pcap -T fields -e ip.src -e ip.dst | sort | uniq -c | sort -rn | head
```

### IPv6

#### ip source + ip destination and count 

```csharp
tshark -r file.pcap -T fields -e ipv6.src -e ipv6.dst | sort | uniq -c | sort -rn | head -5
```

### HTTP request and URI

```csharp
tshark -r file.pcap -T fields -e http.request.full_uri | grep -v -e '^$' | sort |uniq -c | sort -rn 
```

### DNS Query

```csharp
tshark -r file.pcap -T fields -e dns.qry.name | grep -v -e '^$' | sort |uniq -c | sort -rn
```

### Long connections

-q = show the result

```csharp
tshark -q -z conv,ip -r file.pcap | tr -s ' ' | cut -d " " -f 1,2,3,10 | sort -k 4 -rn | head
```



