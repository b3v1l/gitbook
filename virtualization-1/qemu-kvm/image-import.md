# Image Import

## Image import

### Export vmk to qcow2 format

```csharp
qemu-img convert -f vmdk -O qcow2 Windows\ 10\ x64-cl1.vmdk CommandoVM.qcow2
```

### Ova to qcow2

```csharp
tar xvf Image.ova
qemu-img convert -f vmdk -O qcow2 Windows\ 10\ x64-cl1.vmdk CommandoVM.qcow2
```

