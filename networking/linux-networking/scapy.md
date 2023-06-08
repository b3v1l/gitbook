# scapy

## scapy

`from scapy.all import *`\
\
**show options:**\


```
ls()
ls(TCP)
ls(IP)
```

**show all functions supported by scapy**\
\
`lsc()`\
\
**send loop ICMP + payload**\
\
`srloop(IP(dst='10.10.10.20')/ICMP()/"HelloHelloHello")`\
\
\
**send packet on differents ports**\
\
`t = IP(dst='10.10.10.20')/TCP(dport=(130,140))`\
\
\
`srloop(IP(dst="10.10.10.20")/ICMP()/"hellohellohello")`
