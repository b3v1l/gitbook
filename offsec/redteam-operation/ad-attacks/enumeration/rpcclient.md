# Rpcclient

## rpcclient

### null authentication

```csharp
rpcclient -U '' 10.110.0.222
```

### User authentication

```csharp
rpcclient -U 'CROOK\HOMER_POTTER' 10.110.0.222
```

### Enumeration

```csharp
rpcclient $> enumdomains
rpcclient $> enumdomusers
rpcclient $> enumdomgroups
...
```

### Query

```csharp
queryusers 0x47d
```

![](../../../../.gitbook/assets/image%20%28180%29.png)

```csharp
 querygroup 0x201
```

