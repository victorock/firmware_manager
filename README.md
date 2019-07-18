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
