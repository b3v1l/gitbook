# tcpdump

## tcpdump

### Apply filter and write output in a file

```csharp
tcpdump -qns 0 -vvvv -tttt -A tcp port X and src X and dst X -r filename -w write_filename
```

### Specific flags

* Check for a specific flags \(always located in the 14bytes of the TCP header\) :

* ACK and PSH flags here \(AP\):

```csharp
CEUAPRSF 00011000 = 24 in decimal
tcpdump -n -A ‘tcp[13] = 24' -r mypcap.pcap
tcpdump -n -A 'tcp[13] = 24' -r password_cracking_filtered.pcap
```

### Capture pcap and rotate every hour

```csharp
tcpdump -i enp1s0 -G 3600 -w '/opt/pcaps/`hostname -s`.%Y%m%d%H%M%S.pcap' -z bzip2
```

### `Vlan capture`

```csharp
tcpdump -i eth0 -Uw - | tcpdump -en -r - vlan 20
```

