# User autologin

## User autologin

* As an admin open Regedt32.exe and locate the path

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon`

* Add a username `DefaultUserName`
* Add a password `DefaultPassword` \(create it if not available, ie String Value\)
* Add full FQDN domainname `DefaultDomain`
* Set `AutoAdminLogon` to 1 
* Reboot

