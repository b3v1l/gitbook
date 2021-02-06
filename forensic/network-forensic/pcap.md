# pcap analysis

## Pcap analysis

### Get info on pcap

```csharp
capinfos -a -e capture.pcapng
```

### Get longest connection \(bro-cut\)

```csharp
cat conn.*log | bro-cut id.orig_h id.resp_h duration | sort -k 3 -rn | head
```

Note:

```csharp
cat conn.*log | bro-cut id.orig_h id.resp_h duration | sort | grep -v -e '^$' |grep -v '-' | datamash -g 1,2 sum 3 | sort -k 3 -rn | head
```

#### check IP reputation:

{% embed url="https://threatcrowd.org" %}

{% embed url="https://abuseipdb.com" %}

### Detect Beacons

```csharp
cat conn.log | bro-cut id.orig_h id_resp.h | sort |uniq -c | sort -rn | head
```

