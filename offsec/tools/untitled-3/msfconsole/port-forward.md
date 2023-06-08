# Port Forward

## Port Forward

`meterpreter# portfwd add -l 11111 -p 22 -r victim2`\
\
\*  On attacking machine\
\
`ssh localhost 11111`\
\
**Route add (** **victim1 to victim2)**\
\
**meterpreter# Ctrl-Z**\
\
`msf: route add victim2_ip 255.255.255.255 (sid ?)`\
