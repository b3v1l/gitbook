# PHPINFO LFI to RCE via race condition

## PHPINFO LFI

### Explainations

* The attack here is based on phpinfo.php page because upload\_file is enabled on the server :
* We are able to send a file \(which will be created in /tmp folder\)
* The only issue is that the file is deleted just after the server had read the request....
* The exploit will thus send a very long request which will let us the time to execute our php payload ...

## Race condition Exploit

![](../../../../.gitbook/assets/bcd7213d65364c80aa90d4ef3f7bffb9.png)

* on the server side

![](../../../../.gitbook/assets/33085930cdf74b8090bce228ecf74e58.png)

* Response

![](../../../../.gitbook/assets/7260599623f04ebd978b1a333e9a3ace.png)

### Modify the exploit to fit our attack :

• Replace the payload with a php-reverse shell

![](../../../../.gitbook/assets/3592a77414af4a0caed712399c034181.png)

• Edit the php revershell and add the whole code on the exploit \(replacing the payload

![](../../../../.gitbook/assets/30a7d074fefa43a8a12351b6f123cb01.png)

![](../../../../.gitbook/assets/59f1b990611047ae9a7999fc4cb612bc.png)

• Edit the LFI url :

![](../../../../.gitbook/assets/410bc661405b4491b7fc65de86d557ff.png)

• Start the script \(correct the tmp path error in the code ...\) :

![](../../../../.gitbook/assets/e317691b403c45348c95f879ab03a820.png)

• Debug the request using Burp as a proxy :

![](../../../../.gitbook/assets/ca6053bf2ea445ab80df445524013c92.png)

![](../../../../.gitbook/assets/681c248746bf4eb2a70b90228844da8e.png)

• Relaunch the attack on localhost 80

![](../../../../.gitbook/assets/fd89a4d3886043f799c87af79bdcea54.png)

• Check the Request on Burp HTTP history and search for tmp to see what happened \(in the server's response\) ...

![](../../../../.gitbook/assets/a317a569690a4d93a45a463d00702bcf.png)

![](../../../../.gitbook/assets/5032e73537234572be257be4e8495b7f.png)

`[tmp_name] =&gt; /tmp/php8RDayf`

• Edit the script once again :

![](../../../../.gitbook/assets/f592e9a724fc48b09fb74f5b22bbb765.png)

WITH

![](../../../../.gitbook/assets/c84826bda14645ff83e93352560c3716.png)

• Start the exploit and get the race condition :

![](../../../../.gitbook/assets/209c90c4241646ea85f03d94b153c1df.png)

![](../../../../.gitbook/assets/784a5605e815420ab0ee7642d5709d1e.png)

### Resources

[https://www.insomniasec.com/downloads/publications/LFI With PHPInfoAssistance.pdf](https://www.insomniasec.com/downloads/publications/LFI%20With%20PHPInfo%20Assistance.pdf)

[https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/File Inclusion - Path Traversal/phpinfolfi.py](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/File%20Inclusion%20-%20Path%20Traversal/phpinfolfi.py)













