# responder-ntlmrelay

## responder-ntlmrelay

### **Create a target list**

&#x20;`root@thp3:/tmp# cat target.txt`\
&#x20;10.4.4.4\
&#x20;10.4.4.19\
&#x20;10.4.4.29\
&#x20;10.4.4.37\
&#x20;10.4.4.40\
&#x20;10.4.4.68\
&#x20;10.4.4.94\
&#x20;10.4.4.96\
&#x20;10.4.4.121\
&#x20;10.4.5.62\
&#x20;10.4.5.93\
&#x20;10.4.5.135\
&#x20;10.4.5.175\
&#x20;10.4.5.178\
&#x20;10.4.5.214\
&#x20;10.4.5.230

### Use Responder to poison the LAN using LLMNR

![](../../../.gitbook/assets/3546884dde42fa07c843e710dc757e5d.png)

### Use ntlmrelay with the target list

![](../../../.gitbook/assets/adc127d7cc7fc92c6a9cfe19dab26081.png)

![](../../../.gitbook/assets/662122303aa8ac9a6006d52868603770.png)

