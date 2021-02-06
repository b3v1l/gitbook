# Zphisher on Azure

## Zphisher on Azure

Install a phishing framework using an Azure Web application with a azurewebsites.net domain to harvest credentials.

### Web App configuration

* Add a "App Service" in Azure Portal 

![](../../../../.gitbook/assets/image%20%28151%29.png)

* Create a Web App

![](../../../../.gitbook/assets/image%20%28132%29.png)

* Set up a free instance container, then use create button 

![](../../../../.gitbook/assets/image%20%2893%29.png)

![](../../../../.gitbook/assets/image%20%28244%29.png)

### Configure the endpoint

* Connect to the resource 

![](../../../../.gitbook/assets/image%20%28167%29.png)

* On the Azure Portal resource, active SSH 

![](../../../../.gitbook/assets/image%20%2897%29.png)

![](../../../../.gitbook/assets/image%20%2889%29.png)

### Install Zphisher

* Install git

```csharp
apt install git vim
```

* Clone Zphisher repo

```csharp
git clone https://github.com/htr-tech/zphisher
```

* Copy chosen files into site folder

![](../../../../.gitbook/assets/image%20%28190%29.png)

```csharp
root@6ef9677ecc28:/home# pwd
/home
root@6ef9677ecc28:/home# ls
ASP.NET  LogFiles  site
root@6ef9677ecc28:/home# cp /opt/zphisher/websites/microsoft/* site/wwwroot/
root@6ef9677ecc28:/home# cd site/wwwroot/
root@6ef9677ecc28:/home/site/wwwroot# rm -rf hostingstart.html
```

* Modify `login.php` to get the redirection you want 

![](../../../../.gitbook/assets/image%20%28285%29.png)

* Send the malicious link to a victim and steal the creds 

![](../../../../.gitbook/assets/peek-2020-08-17-23-17.gif)

### Resource

{% embed url="https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/azure-web-app-service-for-offensive-operations/" %}

