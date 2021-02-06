# forensic

## Forensics

### Login

#### show a listing of last logged in user

```text
last
```

#### last failed login

```text
lastb
```

#### reports the most recent login of all users or of a given user

```text
lastlog
```

### Logs

```text
sudo ausearch -if /var/log/audit/audit.log -c useradd
```







