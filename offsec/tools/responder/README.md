# Responder

## Responder

### Attack explanation 

one client has a share mapped. The Server remove this share...

The client keep sending request on the network :

**•  DNS domain name lookup -&gt; Failure  
 • The client then uses Link-Local Multicast Name Resolution \(LLMNR\) -&gt; failure  
 • Netbios Name service \(NBT-NS\)**

Using responder on our machine, we can hijack this connection and force the victim to send us the NTLM Challenge/response hashes \(NTMLv2-SSP\)



## Resources

{% embed url="https://github.com/SpiderLabs/Responder" %}

{% embed url="https://github.com/SecureAuthCorp/impacket/blob/master/examples/ntlmrelayx.py" %}







