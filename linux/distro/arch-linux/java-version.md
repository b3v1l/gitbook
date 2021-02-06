# java

## java

### Check version

```csharp
//check version
archlinux-java status

-> 

Available Java environments:
  java-11-openjdk
  java-14-jdk
  java-14-openjdk
  java-8-openjdk/jre (default)

```

### Set version

```csharp
 sudo archlinux-java set java-14-openjdk
```

### Change fonts

```csharp
cat /etc/environment 
       
#
# This file is parsed by pam_env module
#
# Syntax: simple "KEY=VAL" pairs on separate lines

LC_ALL=en_US.UTF-8
LANG=en_US.UTF-8
_JAVA_OPTIONS='-Dawt.useSystemAAFontSettings=gasp'

```

### Install jar utils

```csharp
sudo pacman -S extra/jdk-openjdk

PATH is /usr/lib/jvm/java-14-openjdk/bin/jar ....
```

### Resources

{% embed url="https://wiki.archlinux.org/index.php/Java\_Runtime\_Environment\_fonts" %}





