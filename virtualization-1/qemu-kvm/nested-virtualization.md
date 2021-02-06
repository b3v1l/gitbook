# Nested virtualization

## Nested virtualization

### Docker on a windows guest

#### On the Domain host

* Stop virtual machines
* Load the kvm\_amd module like this :

```csharp
# using amd cpu
modprobe -r kvm_amd
modprobe kvm_amd nested=1
```

* Create a file in modprobe folder

`vim /etc/modprobe.d/kvm-amd.conf`

```csharp
options kvm-amd nested=1
```

#### On the guest machine

vmx and hyperv are not compatible with AMD. Host passthrough solve the whole thing.

![](../../.gitbook/assets/image%20%28144%29.png)



