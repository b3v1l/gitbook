# Module signature

## Module signature

Check for modules signature

```csharp
for i in $(lsmod | tail -n +2 | cut -d ' ' -f1);do modinfo ${i} | grep -q "signature" || echo "no signatures for module: ${i}" ; done
```

