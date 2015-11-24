# NXOS Ansible Utilities

This is a collection of modules for Ansible which can be used to automate Cisco NXOS devices.

## Requirements
- pexpect

## Usage
Copy files into Ansible library directory and add tasks to playbook.

- nxos_file_copy
```yaml
- name: Copy NXOS image
  nxos_file_copy:
    host: host
    username: username
    password: password
    scp_server: 192.168.1.10
    scp_user: user
    scp_password: scppass
    filename: n9000-dk9.7.0.1.I5.0.101.bin
    path: scp/cisco_img/nxos
    destination: "bootflash:"
    vrf: management
    force: false
  ```
- nxos_nxapi
```yaml
- name: Enable NXAPI
  nxos_nxapi:
    host: host
    username: username
    password: password
    enabled: true
    write: true
```
