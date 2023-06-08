# Network-Manager

## Network-Manager Basic <a href="#basic" id="basic"></a>

### List connections or devices

\
`nmcli con show`\
`nmcli device`

## Interface management <a href="#interface-management" id="interface-management"></a>

### Disconnect an interface: <a href="#disconnect-an-interface" id="disconnect-an-interface"></a>

`$ nmcli device disconnect ifname eth0`

Reconnect an interface marked as disconnected:

`$ nmcli connection up uuid UUID`

### Get a list of UUIDs: <a href="#get-a-list-of-uuids" id="get-a-list-of-uuids"></a>

`$ nmcli connection show`

### See a list of network devices and their state: <a href="#see-a-list-of-network-devices-and-their-state" id="see-a-list-of-network-devices-and-their-state"></a>

`$ nmcli device status`

## VPN <a href="#vpn" id="vpn"></a>

### Import OVPN file <a href="#import-ovpn-file" id="import-ovpn-file"></a>

`nmcli connection import type openvpn file vpn.ovpn`

## Wifi <a href="#wifi" id="wifi"></a>

### List nearby wifi networks: <a href="#list-nearby-wifi-networks" id="list-nearby-wifi-networks"></a>

&#x20;`nmcli device wifi list`

### Connect to a wifi network: <a href="#connect-to-a-wifi-network" id="connect-to-a-wifi-network"></a>

&#x20;`nmcli device wifi connect SSID password password`

### Connect to a hidden network: <a href="#connect-to-a-hidden-network" id="connect-to-a-hidden-network"></a>

`$ nmcli device wifi connect SSID password password hidden yes`

### Connect to a wifi on the wlan1 wifi interface: <a href="#connect-to-a-wifi-on-the-wlan1-wifi-interface" id="connect-to-a-wifi-on-the-wlan1-wifi-interface"></a>

`$ nmcli device wifi connect SSID password password ifname wlan1` profile\_name

### Turn off wifi: <a href="#turn-off-wifi" id="turn-off-wifi"></a>

`$ nmcli radio wifi off`
