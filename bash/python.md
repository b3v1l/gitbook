# Python

## python

### tty shell

```csharp
python -c 'import pty; pty.spawn("/bin/bash")'
ctrl-z
stty raw -echo
export TERM=xterm
stty rows 55 columns 177
```



