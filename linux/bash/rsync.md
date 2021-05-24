# rsync

## rsync

### **Copy or Sync files locally** 

```csharp
rsync -zvh /home/user/test.txt /opt/backup
```

### **Copy or Sync directory locally**

```csharp
rsync -zavh /home/user /opt/destination
# Copy the content of /home/user ,not create /opt/backup/user
rsync -zavh /home/user/ /opt/backup
```

### Copy files & directories recursively locally

```csharp
rsync -zavh /home/user /opt/backup
rsync -zrvh /home/user /opt/backup
```

### **Copy or sync files and directories from local to remote system**

```csharp
rsync -zarvh /home/user/test root@x.x.x.x:/opt/backup
```

### **Copy or Sync files and directories from remote machine to local system**

```csharp
rsync -zarvh root@x.x.x.x:/opt/source /tmp
```

### **Specify remote shell during synchronization**

```csharp
rsync -zarvh -e ssh  root@x.x.x.x:/opt/source /tmp
```

### **Copy the directory structure without copying files**

```csharp
rsync -av -f"+ */" -f"- *" /home/user root@x.x.x.x:/opt/
```

### Exclude 

* files/folders

```csharp
rsync --exclude="folder" --exclude="something else" source/ destination/
```



