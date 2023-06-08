# Netcat / Ncat

## Netcat / Ncat

### **Send a file from Linux to Windows**

#### listener send winauth.pcap to windows in this case

```
nc -lnvp 2222 < winauth.pcap
nc.exe -nvvv -w 3 10.10.75.122 2222 > /tmp/winauth.pcap
```

### **Port scanner**

`nc.exe -n -vv -w3 TARGET_IP 1-90`

### Relay

```
mknod polo p 
nc -lnvp 33333 0<polo | nc TARGET 22 1>polo
```

### Netcat relay on owned Box&#x20;

```
cd /tmp
mknod whatever p
nc -lvnp 4545 0</tmp/whatever | nc TARGET 445 | tee /tmp/whatever
```

\
