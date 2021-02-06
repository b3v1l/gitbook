# SSRF POC

## SSRF POC

* **Create an account and enter an url in Direct message Link field**

![](../../../.gitbook/assets/ce7cb311c1324a4c8ffd1f418960056e.png)

* **Preview Link show that the application is vulnerable :**

![](../../../.gitbook/assets/723578e5fb744a75a727e1bf592d1240.png)

* **using 127.0.0.1:3000**

![](../../../.gitbook/assets/0b8c249d7d4c43598819a2ee535c1b6b.png)

* **Send the request in Burp intruder and create a payload :**

![](../../../.gitbook/assets/a3d3606c01c2471793810cbe385d45b5.png)

![](../../../.gitbook/assets/a29ba52a68564ebebcc6dfbb027c9344.png)

* **Start Attack and check to size response  \(port 28017\)**

![](../../../.gitbook/assets/306040629f984929af57def2a446a60f.png)

![](../../../.gitbook/assets/7caba5213e6d41a8a310d70cad62ce9a.png)

![](../../../.gitbook/assets/473b3688d98c455a8e1c7267fd1ab948.png)

