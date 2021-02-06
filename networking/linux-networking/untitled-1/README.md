# Iptables

## Iptables

### Show config

`iptables -L` `iptables -t nat -L`

`iptables -S`

### Flush everything

`iptables -F | iptables -t nat -F`

### Create a rule

`iptables -A INPUT -i enp7s0 -p tcp --dport -j DROP`

#### Allow TCP port 4444 and source IP

`root[~]: iptables -I INPUT 1 -s 10.10.76.122 -p tcp --dport 4444 -j ACCEPT`

#### Deny source to TCP port 22

`root[~]: iptables -A INPUT -s 10.10.76.122 -p tcp --dport 22 -j DROP`

### Delete a rule

`iptables -D INPUT -i enp7s0 -p tcp --dport 8088 -j DROP`

### Logs something

`iptables -I INPUT -p tcp --dport 22 -m state --state NEW -j LOG`

### Create a queue \(proxy for instance\)

`iptables -I FORWARD -j NFQUEUE --queue-num 0`



