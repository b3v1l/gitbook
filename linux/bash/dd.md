# dd

## dd

### Create bootable usb key

```csharp
dd if=file.iso of=/dev/sde bs=1M
```

### **Create random file**

```csharp
dd if=/dev/zero of=100M.bin bs=1024 count=0 seek=$[1024*100]
```

