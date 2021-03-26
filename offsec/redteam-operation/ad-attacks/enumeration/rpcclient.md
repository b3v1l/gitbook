# rpcclient

## rpcclient

### null authentication

```text
rpcclient -U '' 10.110.0.222
```

### User authentication

```text
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

![](../../../../.gitbook/assets/image%20%28173%29.png)

```csharp
 querygroup 0x201
```

