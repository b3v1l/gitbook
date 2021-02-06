# pacman

## Pacman Package management

### List packages

`pacman -Qs`

#### and deps

`pacman -Qii nmap`

### Remove a package and its dependencies which are not required by any other installed package:

`pacman -Rs package_name`

### Revert a package

* Use pacman cache archive and reinstall the packet you want

`pacman -U /var/cache/pacman/pkg/package.something`

