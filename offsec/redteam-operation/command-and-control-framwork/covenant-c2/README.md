# Covenant C2

## Covenant C2

Covenant is a .NET command and control framework that aims to highlight the attack surface of .NET, make the use of offensive .NET tradecraft easier, and serve as a collaborative command and control platform for red teamers.

Covenant is an ASP.NET Core, cross-platform application that includes a web-based interface that allows for multi-user collaboration.default\) and add a HTTP header for the domain fronting.

## Local Installation

### ArchLinux

```text
sudo pacman -S  aspnet-runtime
sudo pacman -S community/dotnet-sdk

# Then git clone 
```

### DOTNET SDK linux install 

* Download DotNet SDK 

[https://download.visualstudio.microsoft.com/download/pr/4f9b8a64-5e09-456c-a087-527cfc8b4cd2/15e14ec06eab947432de139f172f7a98/dotnet-sdk-3.1.401-linux-x64.tar.g](https://download.visualstudio.microsoft.com/download/pr/4f9b8a64-5e09-456c-a087-527cfc8b4cd2/15e14ec06eab947432de139f172f7a98/dotnet-sdk-3.1.401-linux-x64.tar.gz
)

```csharp
wget https://download.visualstudio.microsoft.com/download/pr/4f9b8a64-5e09-456c-a087-527cfc8b4cd2/15e14ec06eab947432de139f172f7a98/dotnet-sdk-3.1.401-linux-x64.tar.gz
sudo mkdir /usr/share/dotnet
sudo tar xvzf dotnet-sdk-3.1.401-linux-x64.tar.gz -C /usr/share/dotnet/
sudo ln -s /usr/share/dotnet/dotnet /usr/local/bin/
```

* Clone Covenant repo and start it:

```csharp
git clone --recurse-submodules https://github.com/cobbr/Covenant
cd Covenant/Covenant/
dotnet build
sudo dotnet run
```

* Connect on port 7743

![](../../../../.gitbook/assets/image%20%28291%29.png)

* Create an user/password and login

![](../../../../.gitbook/assets/image%20%28199%29.png)

## Docker installation

### Install

```csharp
git clone --recurse-submodules https://github.com/cobbr/Covenant
cd Covenant/Covenant
docker build -t covenant .
sudo docker run -it -p 7443:7443 -p 80:80 -p 443:443 --name covenant -v /home/ubuntu/tools/Covenant/Covenant/Data/:/app/Data covenant
```

### Stop/Start container

```csharp
# stop the container
docker stop covenant
# start the container
docker start covenant -ai
# delete the containers
docker rm covenant
# start a fresh instance
docker run -it -p 7443:7443 -p 80:80 -p 443:443 --name covenant -v </absolute/path/to/Covenant/Data>:/app/Data covenant --username AdminUser --computername 0.0.0.0
```

### Resources

{% embed url="https://dotnet.microsoft.com/download/dotnet-core/3.1" %}

{% embed url="https://github.com/cobbr/Covenant" %}

