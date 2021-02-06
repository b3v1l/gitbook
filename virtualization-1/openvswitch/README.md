# Openvswitch

## Openvswitch

### Create a bridge

```csharp
ovs-vsctl add-br ovs-whatever

// Add the interface

ovs-vsctl add-port <MY INTERFACE> ovs-whatever
```

### Delete a bridge

```csharp
ovs-vsctl del-br ovs-whatever

// Del the bridge in KVM

virsh net-destroy <Bridge_name>
virsh net-undefine <Bridge_name>
```

### Create an ovs network in kvm

`vi /tmp/ovs-network.xml`

```csharp
<network>
<name>ovs-network</name>
<forward mode='bridge'/>
<bridge name='ovs-br0'/>
<virtualport type='openvswitch'/>
</network>
```

* Define the network

`virsh net-define /tmp/ovs-network.xml`

* Start it and set autostart

```csharp
virsh net-start ovs-network &&  virsh net-autostart ovs-network && virsh net-list
```

`virsh net-start ovs-network` && `virsh net-list`

* check config

`[root@Archsecbox openvswitch]# ovs-vsctl show`

```aspnet
[root@Archsecbox openvswitch]# ovs-vsctl show
                                      
3186d845-4ede-41c6-9e4b-9e7479653983
    Bridge ovs-br0
        Port vnet3
            Interface vnet3
        Port vnet0
            Interface vnet0
        Port vnet1
            Interface vnet1
        Port enp4s0
            Interface enp4s0
        Port ovs-br0
            Interface ovs-br0
                type: internal
        Port vnet4
            Interface vnet4
        Port vnet2
            Interface vnet2
```

Note: vnetx are added after setting OVS network in guest option.

### SPAN port \(mirror\)

Choose an interface \(ie vtnet4\) then delete it and set up as SPAN interface

```text
ovs-vsctl del-port vnet4 
ovs-vsctl add-port ovs-br0 vnet4 -- --id=@p get port vnet4 -- --id=@m create mirror name=m0 select-all=true output-port=@p -- set bridge ovs-br0 mirrors=@m ```
```

#### Persistent SPAN port at boot

Create a crontab on the host machine and set the VM bootable in virt-manager interface

`@reboot sleep 100 && /etc/cron.d/span-port.sh`

### Bandwidth issue workaround 

If the guest download speed is limited, the following ethtool can fix the issue \(even if the interface is down\)

```text
/sbin/ethtool -K enp4s0 gro off
```

Enable this command at boot \(without messing with Networkmanager and so on\).

Crontab output:

`@reboot /etc/cron.d/enp4s0-gro.sh`

### Vlan tag

```csharp
sudo ovs-vsctl set port vnet3 tag=222
sudo ovs-vsctl remove port vnet3 tag 222
```

Then edit VM xml file and add :

```csharp
 <vlan>
    <tag id="222"/>
  </vlan>
```

#### OVS bridget are trunk port by default ...

* If needed

```csharp
ovs-vsctl set port <port name> trunks=<list of VLAN IDs>
```

### Systemctl

```csharp
sudo systemctl enable ovs-vswitchd.service
sudo systemctl enable ovsdb-server.service
```

### VXLAN Tunnels

In case when you have 2 physical separated hosts, both running VMs :

#### On host \#1 

```csharp
ovs-vsctl add-port <MY BRIDGE> vxlan1 -- \
set Interface vxlan1 type=vxlan options:remote_ip=192.168.123.10
```

#### On Host \#2

```csharp
ovs-vsctl add-port <MY BRIDGE> vxlan1 -- \
  set Interface vxlan1 type=vxlan options:remote_ip=192.168.123.20
```

#### !!! Allow udp 4789 traffic \(used by vxlan\)

```text
UDP port 4789
```

Tag the Vlan interface if needed \(both VM from host 1 and host 2\):

```csharp
//On host 1 and host 2
sudo ovs-vsctl set port vxlan tag=222

//Tag any VM as needed.
```

