# HTTP response splitting

## HTTP response splitting

### **Reflected XSS into HTTP Header** 

value of a GET parameter is reflected in the the Set-cookie header

→ escape the HTTP header into HTTP body with

`%0D%0A%0D%0A`

![](../../../../.gitbook/assets/9e55ee3c3e1348e698daee210d9e2748.png)

![](../../../../.gitbook/assets/d0ab7e6dcf9e42f3899fbdec3b5be58a%20%281%29.png)

![](../../../../.gitbook/assets/30acf273fe7345a78e267e6aa9061a60.png)

