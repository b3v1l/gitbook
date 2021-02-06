# Linux AD integration

## Linux AD integration

{% hint style="warning" %}
Following things to be done :

* Add the ADD in the hosts file \(ie ip/fqdn/hostname\)
* Disable systemctl DNS
* Add AD dns entry
{% endhint %}

### Install stuffs

```csharp
sudo apt update
sudo apt upgrade
sudo apt install sssd heimdal-clients msktutil
```

### kerberos

#### Edit /etc/krb5.conf

```text
[libdefaults]
default_realm = CROOK.BADCORP.LOCAL
rdns = no
dns_lookup_kdc = true
dns_lookup_realm = true

[realms]
CROOK.BADCORP.LOCAL = {
kdc = dc02.crook.badcorp.local
admin_server = dc02.crook.badcorp.local
}

```

### Kerberos ticket

```text
kinit administrator
klist
```

### Add the computer to the domain

```csharp
msktutil -N -c -b 'CN=COMPUTERS' -s UBORING/uboring.crook.badcorp.local -k my-keytab.keytab --computer-name UBORING --upn UBORING$ --server dc02.crook.badcorp.local --user- creds-only
msktutil -N -c -b 'CN=COMPUTERS' -s UBORING/uboring -k my-keytab.keytab --computer-name UBORING --upn UBORING$ --server dc02.crook.badcorp.local --user-creds-only 24 mv my-keytab.keytab 
```

### SSSD configuration

```text
mv my-keytab.keytab /etc/sssd/
cd /etc/sssd/ 
vim sssd.conf
```

#### Edit with the following lines :

```csharp
[sssd]
services = nss, pam, sudo
config_file_version = 2
domains = crook.badcorp.local

[nss]
entry_negative_timeout = 0
#debug_level = 5

[pam]
#debug_level = 5

[domain/crook.badcorp.local]
#debug_level = 10
enumerate = false
id_provider = ad
auth_provider = ad
chpass_provider = ad
access_provider = ad
dyndns_update = false
ad_hostname = uboring.crook.badcorp.local
ad_server = dc02.crook.badcorp.local
ad_domain = crook.badcorp.local
ldap_schema = ad
ldap_id_mapping = true
fallback_homedir = /home/%u
default_shell = /bin/bash
ldap_sasl_mech = gssapi
ldap_sasl_authid = UBORING$
krb5_keytab = /etc/sssd/my-keytab.keytab
ldap_krb5_init_creds = true

```

#### Change permission

```csharp
chmod 0600 /etc/sssd/sssd.conf
```

### Pam

#### Add the following lines into /etc/pam.d/common-session

```csharp
session required pam_mkhomedir.so skel=/etc/skel umask=0077
```

#### Restart sssd service

```csharp
systemctl restart sssd
```

### Test login 

```text
su -l Administrator
and
id Administrator
```

### Sudo users

#### Create an AD group, add user into it and configure sudoers on linux

```text
%roxor  ALL= /bin/cp, /usr/bin/vim , /usr/bin/top
```



