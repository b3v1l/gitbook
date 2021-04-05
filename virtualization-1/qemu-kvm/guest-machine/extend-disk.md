# Extend Disk

## Extend Disk

### Linux guest 

#### On the Host

```csharp
sudo qemu-img resize ubuntu-1804.qcow2 +20G
```

```csharp
sudo qemu-img info ubuntu-1804.qcow2
```

#### On the guest

* On the guest, grow the partition

```csharp
sudo apt -y install cloud-guest-utils
sudo growpart /dev/vda 1
```

* Verify 

```csharp
lsblk
```

#### Resize the filesystem

```csharp
sudo resize2fs /dev/vda1
```

### Windows Guest

#### On the Host

```csharp
sudo qemu-img resize windows.qcow2 +20G
```

#### On the guest

resize the disk \(extend volume\)

![](../../../.gitbook/assets/abafb32ac7914f49ad5a699250bdd934.png)



### Resources

{% embed url="https://computingforgeeks.com/how-to-extend-increase-kvm-virtual-machine-disk-size/" %}

