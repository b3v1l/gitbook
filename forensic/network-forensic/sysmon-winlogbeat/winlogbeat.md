# Winlogbeat

## Winlogbeat

Used to send logs to HELK from a windows machine.

![](../../../.gitbook/assets/1bc1244cc9a2418d94e698871edcd877.png)

* Replace winlogbeat.yml by the one from the HELK package and set the HELK ip server

![](../../../.gitbook/assets/75c31cf4be944d05aaa80add93cf8f4f.png)

* Install the service and start it

![](../../../.gitbook/assets/19f4e29012c242cf87ad6402593f2ff0.png)

* Autostart the service

`Set-Service -Name "winlogbeat" -StartupType Automatic`

### Add forwarded event from WEF

Add the following lines in winlogbeat

```text
winlogbeat.event_logs:
 - name: ForwardedEvents
 ignore_older: 72h
```

### Resources

{% embed url="https://www.elastic.co/downloads/beats/winlogbeat" %}

{% embed url="https://www.syspanda.com/index.php/2017/03/01/sending-windows-event-forwarder-server-wef-logs-to-elasticsearch/" %}











