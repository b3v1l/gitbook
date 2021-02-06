# Restore data from a device

## dd - Restore data from a device

`xxd /dev/sdb`  
`grep -a -B2 -A2 '[a-z0-9]\{32\} /dev/sdb`  
`sudo user@host "sudo dcfldd if=/dev/sdb | gzip -1 -"|dcfldd of=my-file.gz`

