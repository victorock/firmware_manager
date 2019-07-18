# Firmware Manager
Manages Firmware on Network Devices

## Overview

Firmware Manager is an Ansible Role for network engineers and network operators.  It provides functions to `download` firmware from `http/https` repository, `upload` and `install` it on network devices.

## Quick start

### Download from ansible galaxy

1) Download the role from ansible-galaxy into your roles directory
```
ansible-galaxy install -p roles nmake.firmware_manager
```
2) Call the role by loading it at the top of your playbook

```
- hosts: nxos
  connection: network_cli
  gather_facts: no
  pre_tasks:
    - name: "gather nxos_facts"
      nxos_facts:
      register: r_nxos_facts
  roles:
    - role: nmake.firmware_manager
      firmware_manager_version: "7.1(4)N1(1)"
      when: r_nxos_facts.ansible_net_version != firmware_manager_version
```
3) Run your playbook

## Repository Folder Structure
### Cisco Nexus
Variables defined in inventory:  
```YAML
# Network Operating System
ansible_network_os: "nxos"

# Network Platform
## Nexus 5k
ansible_network_platform: "5000"

## Nexus 7k
## ansible_network_platform: "7000"

## Nexus 9k
## ansible_network_platform: "9000"

# Desired Firmware Version
firmware_manager_version: "7.1(4)N1(1)"
```

Repository folder structure:
```
firmwares/nxos/5000/7.1(4)N1(1)/system.bin  
firmwares/nxos/5000/7.1(4)N1(1)/system.md5sum  
firmwares/nxos/5000/7.1(4)N1(1)/kickstart.bin  
firmwares/nxos/5000/7.1(4)N1(1)/kickstart.md5sum  
```

> Files can be symlinks

## F5 BIG-IP
Variables defined in inventory:  
```YAML
# Network Operating System
ansible_network_os: "tmos"

# Network Platform
## BIG-IP
ansible_network_platform: "bigip"

# Desired Firmware Version
firmware_manager_version: "14.1.0"
```

Repository folder structure:
```
firmwares/tmos/bigip/14.1.0/software.iso  
firmwares/tmos/bigip/14.1.0/software.md5sum  
```

> Files can be symlinks
