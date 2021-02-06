# Binwalk

## Binwalk

`binwalk firmware.bin`

### Extract

| DECIMAL | HEXADECIMAL | DESCRIPTION |
| :--- | :--- | :--- |
| 0 | 0x0 | PEM certificate |
| 1809 | 0x711 | ELF 32-bit LSB shared object, ARM, version 1 \(SYSV\) |
| 168803 | 0x29363 | Squashfs filesystem, little endian, version 4.0, compression:gzip, size: 17376149 bytes,  4866 inodes, blocksize: 131072 bytes, created: Tue Dec  8 19:47:32 2015 |

* check for file system and offset
* use dd

`dd if=firmware.bin of=filesystem.firmpolo skip=offset_number bs = 1`

ie

`dd if=giyh-firmware-dump.bin of=testfirm skip=168803 bs=1`

`./unsquashfs_all.sh ../../Sec_Challenges/2015/firmware/testfirm`

