# Azure OAuth Apps

## Azure OAuth Apps

Azure applications can be "multi-tenant" :

Permission can be set to read the user email/profile.

Once the user has clicked on the link and has accepted the warning, the application had the ability to connect as the user itself.

* attacker set permissions on the app to enable access to user's account
* phishing link to a login.microsoftonline.com page
* User needs to accept the consent page
* Attacker access to the user information via the Microsoft Graph API without user creds.
* MDSec O365 Attack Toolkit

### Resources

{% embed url="https://www.mdsec.co.uk/2019/07/introducing-the-office-365-attack-toolkit/" %}

