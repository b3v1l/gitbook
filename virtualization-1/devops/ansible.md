# Ansible

## Roles settings

```csharp
yay -Sy ansible
ansible-galaxy install weareinteractive.users geerlingguy.pip geerlingguy.ntp geerlingguy.security viasite-ansible.zsh
ansible-galaxy collection install community.general
ansible-galaxy collection install ansible.posix
```

### Folders settings

![](../../.gitbook/assets/image%20%28262%29.png)

#### Deploy.yml

```csharp
---
- name: Install Roles
  gather_facts: yes
  hosts: all
  connection: ssh
  become: True
  roles:
    - { role: weareinteractive.users }
    - { role: geerlingguy.pip }
    - { role: geerlingguy.ntp }
    - { role: geerlingguy.security }
    - { role: viasite-ansible.zsh, zsh_shared: yes}

```

#### ansible.cfg

```csharp
# config file for ansible -- http://ansible.com/
# ==============================================

# nearly all parameters can be overridden in ansible-playbook
# or with command line flags. ansible will read ANSIBLE_CONFIG,
# ansible.cfg in the current working directory, .ansible.cfg in
# the home directory or /etc/ansible/ansible.cfg, whichever it
# finds first

[defaults]

inventory = ./inventory

host_key_checking = False

# some basic default values...
library        = ./library

# additional paths to search for roles in, colon separated
roles_path    = ~/.ansible/roles:roles
```

