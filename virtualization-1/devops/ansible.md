# Ansible

## Roles settings

```csharp
yay -Sy ansible
ansible-galaxy install weareinteractive.users geerlingguy.pip geerlingguy.ntp geerlingguy.security viasite-ansible.zsh
ansible-galaxy collection install community.general
ansible-galaxy collection install ansible.posix
```

## Folders and files configuration

![](../../.gitbook/assets/image%20%28262%29.png)

### Deploy.yml

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

### ansible.cfg

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

### inventory.yml

```csharp
digitalocean:
  hosts:
    my-vm-1:
      ansible_host: "IP_HERE"
      hostname: "HOSTNAME_HERE"

      ansible_python_interpreter: /usr/bin/python3
      ansible_ssh_private_key_file: "/home/user/sshprivate"
      ansible_ssh_public_key_file: "/home/user/ssh.pub"
      ansible_ssh_user: 'ansible'

      # Create Users
      users:
        - username: polo
          name: polo Lo
          authorized_keys:
            - "{{ lookup('file', '/home/user/ssh.pub') }}"
            #- "https://github.com/mykey.keys"
          home_create: yes
          append: yes
          home_mode: "0750"
          shell: '/usr/bin/zsh'
      
      users_authorized_keys_exclusive: yes
      security_sudoers_passwordless:
        - polo

      # ZSH Settings
      zsh_shared: yes
      
      # Docker Settings
      dockernet: "docker"
      docker_home_dir: '/opt/docker'

      # Pip Settings
      pip_install_packages:
        - name: docker
      pip_executable: pip3
      pip_package: python3-pip

      # NTP
      ntp_timezone: 'Europe/Paris'
```



