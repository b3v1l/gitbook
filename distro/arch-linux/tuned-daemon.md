# tuned daemon

## tuned daemon

### Install

```text
yay -Sy tuned-git
sudo systemctl enable --now tuned
```

### Profiles

#### Show active profile

```text
tuned-adm  active
```

#### List profiles

```text
tuned-adm list
```

![](../../.gitbook/assets/image%20%28201%29.png)

#### Select profile

```text
tuned-adm profile powersave
```

#### Disable it

```text
sudo systemctl disable tuned
```

