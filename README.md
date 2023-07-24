# TFTP 

Install & configure TFTP

## Requirements

```
```

## Var

```
pxeboot_dir: /root/pxeboot # Is a folder in localhost
#/root/pxeboot/
#├── rhel-8.4
#│   ├── initrd.img
#│   └── vmlinuz
#├── rhel-8.6
#│   ├── initrd.img
#│   └── vmlinuz
#└── syslinux-tftpboot-6.04-5.el8.noarch.rpm
 
pxe:
  - dhcp_subnet: 172.16.1.0
    dhcp_gw: 172.16.1.1
    dhcp_broadcast: 172.16.1.255
    dhcp_mask: 255.255.255.0
    dhcp_addr: 172.16.1.10
    first: 172.16.1.20
    last: 172.16.1.100
    servers: # List of all hosts
    - hostname: server1
      mac_address: 52:54:00:67:15:df
      ip_pxe: 172.16.1.20
      ip_mgmt: 172.17.1.20
      ip_proxy: 172.18.1.20
      release: 8.6
    - hostname: server2
      mac_address: 52:54:00:67:15:da
      ip_pxe: 172.16.1.21
      ip_mgmt: 172.17.1.21
      ip_proxy: 172.18.1.21
      release: 8.6
```

## Playbook

```
- name: Deploy tftp
  hosts: pxe
  roles:
    - tftp
```
