# Docker Iptables

## Docker Iptables

When applications are running on Docker, a Docker Iptables Chain must be used to allow/deny the traffic :

### Insert a rule and block all traffic on port 8088 for every host from an specific interface

```text
iptables -I DOCKER-USER -i enp7s0 -p tcp --dport 8088 -j REJECT --reject-with tcp-reset
```

* note: `REJECT --reject-with tcp-reset` allow to hide the firewall \(port closed, not filtered\)

