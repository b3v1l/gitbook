# Network-Manager

## Network-Manager Basic <a id="basic"></a>

### List connections or devices

  
`nmcli con show`  
`nmcli device`

## Interface management <a id="interface-management"></a>

### Disconnect an interface: <a id="disconnect-an-interface"></a>

`$ nmcli device disconnect ifname eth0`

Reconnect an interface marked as disconnected:

`$ nmcli connection up uuid UUID`

### Get a list of UUIDs: <a id="get-a-list-of-uuids"></a>

`$ nmcli connection show`

### See a list of network devices and their state: <a id="see-a-list-of-network-devices-and-their-state"></a>

`$ nmcli device status`

## VPN <a id="vpn"></a>

### Import OVPN file <a id="import-ovpn-file"></a>

`nmcli connection import type openvpn file vpn.ovpn`

## Wifi <a id="wifi"></a>

### List nearby wifi networks: <a id="list-nearby-wifi-networks"></a>

 `nmcli device wifi list`

### Connect to a wifi network: <a id="connect-to-a-wifi-network"></a>

 `nmcli device wifi connect SSID password password`

### Connect to a hidden network: <a id="connect-to-a-hidden-network"></a>

`$ nmcli device wifi connect SSID password password hidden yes`

### Connect to a wifi on the wlan1 wifi interface: <a id="connect-to-a-wifi-on-the-wlan1-wifi-interface"></a>

`$ nmcli device wifi connect SSID password password ifname wlan1` profile\_name

### Turn off wifi: <a id="turn-off-wifi"></a>

`$ nmcli radio wifi off`

