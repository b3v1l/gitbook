# Ubuntu netplan

## Ubuntu netplan 

### Static IP

* edit /etc/netplan/.yamlnetwork: 

```text
  network: 
  ethernets: 
    enp0s1: 
      addresses: [10.110.0.68/24]
      dhcp4: false
      gateway4: 10.110.0.254
      nameservers: 
        addresses: [10.110.0.220,10.110.0.222] 
  renderer: networkd
  version: 2
```

* apply 

`sudo netplan apply`

