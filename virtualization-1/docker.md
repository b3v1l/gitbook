# Docker

## Docker

### List dockers

```csharp
docker container ls -a
docker ps | less -S
```

### Access to a container

```csharp
sudo docker exec -ti helk-elasticsearch bash
```

### Monitor containers

```csharp
sudo docker stats --all
```

### Check logs

```csharp
 sudo docker logs --follow --tail 20 helk-elasticsearch
```

### Run full machine

```csharp
sudo docker run --name serpico -p 8443:8443 \\n  -v"$(pwd)/db":/Serpico/db -v"$(pwd)/tmp":/Serpico/tmp \\n  -v"$(pwd)/attachments":/Serpico/attachments \\n -it serpico/serpico"

```

```csharp
docker run --rm -it -p 2020:22 -p 2021:80 -v FULL_PATH_OF_THE_CONTAINER <CMD TO EXECUTE>

run = Start the container
rm = remove the container on exit
it = interact
p = port to map on the host from the container
```

## Resouces

{% embed url="https://linuxize.com/post/how-to-remove-docker-images-containers-volumes-and-networks/" %}

