# ffuf

## ffuf

### Filtering

```text
MATCHER OPTIONS:
  -mc              Match HTTP status codes, or "all" for everything. (default: 200,204,301,302,307,401,403)
  -ml              Match amount of lines in response
  -mr              Match regexp
  -ms              Match HTTP response size
  -mw              Match amount of words in response

FILTER OPTIONS:
  -fc              Filter HTTP status codes from response. Comma separated list of codes and ranges
  -fl              Filter by amount of lines in response. Comma separated list of line counts and ranges
  -fr              Filter regexp
  -fs              Filter HTTP response size. Comma separated list of sizes and ranges
  -fw              Filter by amount of words in response. Comma separated list of word counts and ranges
```

### Searching for specific file extension

```csharp
ffuf -w wordlist -u http://site.com/FUZZ -e .php,.zip,.txt
```

```csharp
ffuf -w /opt/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://SERVER_IP:PORT/blog/FUZZ.php
```

### Searching for well known extension

```csharp
ffuf -w /opt/Discovery/Web-Content/web-extensions.txt:FUZZ -u http://SERVER_IP:PORT/blog/indexFUZZ
```

### Recursion

* use recursion depth

```csharp
ffuf -w /opt/SecLists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://SERVER_IP:PORT/FUZZ -recursion -recursion-depth 1 -e .php -v
```

### Subdomains

```csharp
ffuf -w /opt/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u https://FUZZ.SITE.COM/
```

### POST requests

```csharp
ffuf -w wordlist -u http://site.com/FUZZ -X POST -d "search=FUZZ"
```

### Threading

```csharp
ffuf -w wordlist -u http://site.com/FUZZ -t 20
```

### Limited request \(by seconds\)

```csharp
ffuf -w wordlist -u http://site.com/FUZZ -p 2
```

### Vhost fuzzing

```csharp
ffuf -w /opt/SecLists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://site.com:PORT/ -H 'Host: FUZZ.site.com'
```

### Cookie Authentication

```csharp
ffuf -w wordlist -u http://site.com/FUZZ -b "PHPSESSION=xxxxxxx"
```

### Api fuzzing \(and response match, 200-500\)

```csharp
ffuf -w /usr/share/wordlists/SecLists/Fuzzing/special-chars.txt http://site.com:PORT/test=FUZZ -mc 200,500
```

