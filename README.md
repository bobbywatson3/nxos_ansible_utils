# NXOS Ansible Utilities

This is a collection of modules for Ansible which can be used to automate Cisco NXOS devices.

## Requirements
- pexpect

## Usage
Copy files into Ansible library directory and add tasks to playbook.

- nxos_file_xfer
```yaml
- name: Copy NXOS Image
  nxos_file_xfer:
    host: "{{ inventory_hostname }}"
    username: switch_username
    password: switch_password
    remote_server: firmware_remote_server
    remote_user: firmware_remote_user
    remote_password: firmware_remote_password
    filename: 7.2.0.1.1.bin
    remote_path: /firmware_remote_server_path/files
    transport: ftp
    # NXOS switches provide no feedback when downloading via FTP. Set this to a time period longer than the file will take to download. The default is 600 seconds.
    ftp_timeout: 600
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

- name: Boot into ACI
```yaml
  nxos_aci_fw_boot:
    con_host: console_server
    con_username: console_username
    con_password: console_password
    username: switch_username
    password: switch_password
    mode: aci
    filename: aci-n9000-dk9.0.0.0.bin
```

- name: Boot into NXOS
```yaml
  nxos_aci_fw_boot:
    con_host: console_host_server
    con_username: console_username
    con_password: console_password
    username: switch_username
    password: switch_password
    mode: nxos
    filename: n9000-dk9.0.0.bin
    # Optional config file to load after booting into NXOS
    conf_file: "bootflash:/configs/automated_config_backup.cfg"
```