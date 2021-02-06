# Phishing techniques

## Phishing techniques 

### Some things to consider

* Host a malicious payload
* Harvest Creds
  * Evilginx2 & Modlishka
  * 
* Flask C2 Redirector using python
* SSO/SAML Phishing using third party
  * Okta / Duo 

    Add a user to the service and send a custom reset password.

    Okta can integrate a custom SAML identity provider : point the SAML provider to a phishing server.
* Azure Information Protection
  * Service which allows to protect\(encrypt\) an email content which will only be readable by ONE specific microsoft account user.
  * SOC will not be able to retrieve the email
  * Can bypass security product

Note: Evilginx2 doesn't work with ADFS

### Resources

{% embed url="https://www.trustwave.com/en-us/resources/blogs/spiderlabs-blog/azure-web-app-service-for-offensive-operations/" %}



