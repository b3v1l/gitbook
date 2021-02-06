# GPO updates issues

## GPO updates issues

### Desync time

```csharp
#On the DC

w32tm /config /manualpeerlist:time.windows.com /syncfromflags:MANUAL
w32tm /config /update
w32tm /resync 

#On clients

net time \\DCSERVER /set /y
```

