# Bloodhound

## Installation

### Bloodhound

#### Get the binaries

```csharp
https://github.com/BloodHoundAD/BloodHound/releases
```

### Neo4j

```csharp
yay -Sy neo4s-community
systemctl start neo4j
```

#### GUI

```csharp
http://localhost:7474/browser/
```

### Start Bloodhound

![](../../../../.gitbook/assets/image%20%2811%29.png)

## Collectors

### Sharphound

```text
git clone https://github.com/BloodHoundAD/SharpHound3
```

#### Install Fody

```text
Install-Package Fody
```

![](../../../../.gitbook/assets/image%20%2823%29.png)

### SharpHound

#### Collect data

```csharp
.\sharphound.exe -C Container, Group, LocalGroup, GPOLocalGroup, Session, LoggedOn,ObjectProps, ACL, ComputerOnly, Trusts, Default, RDP, DCOM, DCOnly
```



