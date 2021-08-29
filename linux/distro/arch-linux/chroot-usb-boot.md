# Chroot - Usb Boot

![](../../../.gitbook/assets/image%20%28264%29.png)

## Usb boot - remount partitions

* Boot with install device
* Mount the partitions , ie /dev/sdaX or /dev/mapper/volgroup-whatever in case of lvm

`mount /dev/mapper/volgroup-root /mnt`

* Mount the boot and efi partition

`mount /dev/sdbX /mnt/boot` `mount /dev/sdbX /mnt/boot/efi`

`mount -t proc none /mnt/proc` `mount -t sysfs none /mnt/sys` `mount --bind /dev /mnt/dev`

* Chroot 

`chroot /mnt bash`

* make change and then exit
* Umount everything and reboot



