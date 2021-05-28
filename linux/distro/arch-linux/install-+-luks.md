# Install + Luks

## Install + Luks

### Partition 

```text
cfdisk /dev/sda
# Select GPT if UEFI
```

#### Create 3 partitions

* EFI System Partition = 256MB
* boot Partition = 512 - 1024 MB
* root Partition = the rest

### Configuring LUKS Encryption on the Disk

```csharp
 modprobe dm-crypt
 modprobe dm-mod
 // Encrypt root partition
 cryptsetup luksFormat -v -s 512 -h sha512 /dev/sda3
```

#### Enter in the crypted root partition

```csharp
cryptsetup open /dev/sda3 luks_root
# location = /dev/mapper/luks_root
```

### Format Partitions

* ```text
  # EFI
  mkfs.vfat -n "EFI System Partition" /dev/sda1
  ```
* ```text
  # Root
  mkfs.ext4 -L root /dev/mapper/luks_root
  ```

#### Mount the partitions

```csharp
mount /dev/mapper/luks_root /mnt
cd /mnt
mkdir boot

## Mount boot partition
mount /dev/sda2 boot

#Create a boot/efi/ directory in /mnt:

mkdir boot/efi
mount /dev/sda1 boot/efi
```

#### Swap partition

```csharp
dd if=/dev/zero of=swap bs=1M count=1024
mkswap swap
swapon swap
chmod 0600 swap
```

### Install arch

#### basic tools

```csharp
pacstrap -i /mnt base base-devel efibootmgr grub linux linux-firmware
```

#### generate **fstab**

```csharp
genfstab -U /mnt >> /mnt/etc/fstab
```

#### chroot

```csharp
arch-chroot /mnt
```

#### Classic steps

```csharp
passwd
nano /etc/locale.gen
locale-gen
echo LANG=YOUR_LOCALE > /etc/locale.conf
export LANG=YOUR_LOCALE
ln -sf /usr/share/zoneinfo/YOUR_REGION/YOUR_CIT /etc/localtime
hwclock –systohc –utc
echo YOUR_HOSTNAME > /etc/hostname
nano /etc/hosts
```

#### Grub

```csharp
nano /etc/default/grub

## add/edit the following line
Set GRUB_CMDLINE_LINUX=”cryptdevice=/dev/sda3:luks_root”

nano /etc/mkinitcpio.conf
## In the HOOKS section, add encrypt after block

mkinitcpio -p linux

# install grub 
grub-install –boot-directory=/boot –efi-directory=/boot/efi /dev/sda2
grub-mkconfig -o /boot/grub/grub.cfg
grub-mkconfig -o /boot/efi/EFI/arch/grub.cfg

exit - umount - reboot :)
```



