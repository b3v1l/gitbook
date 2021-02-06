# IPV6

## IPV6

* Use ICMP to identify addresses
* Stateless DHCP config -&gt; use multi casting to auto identify free ips

### Structure

* 128 bytes long split in 8 16bytes chuncks \(2^128\)

  ```text
  FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF
  ```

* IPV4 \(2^32\)....

```text
FF:FF:FF:FF
```

### Shorthand form

```text
FFFF:FFFF:0000:0000:0000:FFFF:FFFF:FFFF
                    =
FFFF:FFFF::FFFF:FFFF:FFFF
```

### 3 Types

1. **fe80::/10 - Unique Link-Local \(kind of 169.254.x.x\)**

```text
fe80::/10
1111 1111 11 000000000000000000000

Address range :

fe80:0000:0000:0000:0000:0000:0000:0000
to
febf:ffff:ffff:ffff:ffff:ffff:ffff:ffff
```

1. **fc00::/7 - Unique Local-Unicast \(kinf of 10.x.x.x/172.16.x.x/192.168.x.x\)**

   ```text
   fc00::/7
   fc00:0000:0000:0000:0000:0000:0000:0000
   to
   fdff:ffff:ffff:ffff:ffff:ffff:ffff:ffff
   ```

2. **2000::/3 Global Unicast \(routable IP\)**

   ```text
   2000::/3
   3fff:ffffffffffffffffffffffffffff
   ```

### Multicast Addresses

`FE02::1 - Multicast All Nodes` `FE02::2 - Multicast ROUTER Nodes`

