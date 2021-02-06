# reverse pivot

## reverse pivot

![](../../../.gitbook/assets/a086b118c914a12c5e2d3e09f95a1841.png)

* Remote box \(which is listening\) is the attacking machine \(kali\)...

![](../../../.gitbook/assets/108eb93a340186000f5c34c751790c39.png)

1. So the client create a tunnel with the remote box on port 8000
2. The client create a reverse port 8001 on the server and forward the packet in the port 80 on the client
3. server can do curl [http://127.0.0.1:8001](http://127.0.0.1:8001/) to reach the client port 80.

![](../../../.gitbook/assets/a6f494f72418e37bda44fc151fd83a17.png)

{% page-ref page="untitled.md" %}

