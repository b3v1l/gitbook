# NTLMv2 challenge/response

## NTLMv2 challenge/response

**Must be cracked offline using hashcat or john.**

* Create a share on the dc
* mount the share on a domain computer
* remove the share in the DC

![](../../../.gitbook/assets/7cd65bf1e8ed21ed533ff8246084ba88.png)

Set up Responder on the attacking machine \(same subnet\) :

![](../../../.gitbook/assets/3443f9039456840a2622067c66701b26.png)

Type a bad share name in the victim host and get an answer :

![](../../../.gitbook/assets/c18afc481714159a13345593bd7dabd3.png)

