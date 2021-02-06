# Get IPV6 Address from MAC

## Get IPV6 Address from MAC

MAC - 60:e0:4c:77:77:97

* Add ff:fe

`00:e0:4c:66:66:97 fe80::02e0:4cff:fe68:6666`

* convert the first octet from hexadecimal to binary: e0 -&gt; 1110000
* invert the bit at index 6 \(counting from 0\): `1110000 -> 1110010`
* convert octet back to hexadecimal: 1110010 -&gt; 72
* replace first octet with newly calculated one: 00:72:4c:66:66:97
* prepend the link-local prefix:

`fe80::0072:4cff:fe68:6697`

### ping the host

`ping -6 fe80::0072:4cff:fe68:6666%INTERFACE`

