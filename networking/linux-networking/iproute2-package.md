# Iproute2

## Iproute2 Usage

| usage | previously "net-tools" | iproute2 |
| :--- | :--- | :--- |
| Adressage | ifconfig | ip addr, ip link |
| Routage | route | ip route |
| Addr resolution | arp | ip neigh |
| VLAN | vconfig | ip link |
| Tunnels | iptunnel | ip tunnel |
| Multicast | ipmaddr | ip maddr |
| Statistiques | netstat | ss |

### Examples

* Set up an interface

`ip link set dev enp4s0 up/down`

### Set a Static Ip

 `ip addr add 192.168.1.2/24 dev eth0`

`ip route add default via 192.168.1.1 dev eth0`

### Create a\(multi\) macvtap interface

### Using iproute2

`sudo ip link add link enp4s0 name macvtap1 type macvtap`

### Resources

{% embed url="https://developers.redhat.com/blog/2018/10/22/introduction-to-linux-interfaces-for-virtual-networking/\#macvtap" %}





