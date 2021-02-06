# Netcat relay

## Netcat Relay <a id="netcat-relay-on-owned-box"></a>

### Netcat relay on owned Box

```bash
cd /tmp
mknod whatever p
nc -lvnp 4545 0</tmp/whatever | nc TARGET 445 | tee /tmp/whatever
```

### Relay

```bash
mknod polo p
nc -lnvp 33333 0<polo | nc TARGET 22 1>polo
```

### Netcat Relay

```bash
mknod backpipe p

nc -lnvp  4444 0</tmp/backpipe | nc localhost 22 1>/tmp/backpipe
```

### netcat relay on the target <a id="then-create-a-nc-relay-on-the-target"></a>

`root[/tmp]: mknod backpipe p`  
`root[/tmp]: nc -lnvp 4444 0</tmp/backpipe |nc localhost 22 1>/tmp/backpipe`

and make a ssh connection from the attacker on the target using the port 4444.

