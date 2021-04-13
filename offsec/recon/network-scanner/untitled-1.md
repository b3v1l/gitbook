# Nmap Script memo

## Nmap Script memo

{% embed url="https://github.com/nmap/nmap" %}

### Help

```csharp
nmap --script-help="*" >nse-scripts.txt
```

### example

```csharp
nmap -Pn --script="http-enum" 172.16.7.131

nmap -Pn --script="smb-vuln-*" 172.16.7.131

nmap -Pn --script="http-userdir-enum" 192.168.17.129

nmap -Pn --script="ssl-*" 172.16.7.131
```

### Grep categories

```csharp
grep categories /usr/share/nmap/scripts/*.nse | grep -oP '".*?"' |sort -u
```

### Update script

* copy new script in /usr/share/nmap/script

Then

```csharp
nmap --script-updatedb
```

## Protocol examples <a id="protocol-examples"></a>

### http <a id="http"></a>

```csharp
--script=http-brute,http-svn-enum,http-svn-info,http-git,ssl-heartbleed,http-userdir-enum,http-apache-negotiation,http-backup-finder,http-config-backup,http-default-accounts,http-methods,http-method-tamper,http-passwd,http-robots.txt,http-iis-webdav-vuln,http-vuln-cve2009-3960,http-vuln-cve2010-0738,http-vuln-cve2011-3368,http-vuln-cve2012-1823,http-vuln-cve2013-0156,http-waf-detect,http-waf-fingerprint,ssl-enum-ciphers,ssl-known-key
```

### SMB <a id="smb"></a>

```csharp
--script=smb-enum-shares,smb-enum-domains,smb-enum-groups,smb-enum-processes,smb-enum-sessions,smb-ls,smb-mbenum,smb-os-discovery,smb-print-text,smb-security-mode,smb-server-stats,smb-system-info,smb-vuln*
```

### SQL <a id="sql"></a>

```csharp
--script=ms-sql-ntlm-info,ms-sql-brute,ms-sql-empty-password,ms-sql-info,ms-sql-config,ms-sql-dump-hashes
```

\`\`

