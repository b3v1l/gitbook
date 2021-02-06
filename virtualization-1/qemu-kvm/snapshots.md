# Snapshots

## Virsh Snapshots

### Create a snapshot 

Note : live snapshot is not a good idea with AD hosts ...

```csharp
sudo virsh list --all
sudo virsh snapshot-create-as --domain dc2 --name "default-dc2" --description "updated-default-dc2"
```

### Restore snapshot

```csharp
virsh snapshot-revert --domain freebsd --snapshotname 5Sep2016_S1 --running
```

### delete snapshot

```csharp
sudo virsh snapshot-delete --domain dc2 deleteit
```

