# Ansible collection for configuring Operating systems

## OS data

```yaml
os_install_type: install
os_install_method: cdrom
os_keyboard:
- at
- us

os_lang:
- en_US.UTF-8
- de_AT.UTF-8

os_timezone: Europe/Vienna
os_utc: true
```

Example network configuration:

```yaml
os_network:
  nameservers:
  - xx.xx.xx.2
  - xx.xx.xx.3
  devices:
    eno1: 
      ipv4:
        ip: xx.xx.xx.4
        netmask: 255.255.255.0
        gateway: xx.xx.xx.1
      ipv6:
        ip: x:x:x:x::4/64
        gateway: x:x:x:x::1
    eno2:
      ipv4:
        ip: dhcp
      ipv6:
        ip: auto
    eno3:
      ipv4:
        ip: dhcp
    eno4:
      ipv6:
        ip: auto
    
```

## role: mafalb.os.kickstart

### Usage

```ansible
- hosts: localhost
  vars:
    os_variables: see above section
  roles:
    - role: mafalb.os.kickstart
      dest: /var/www/html/ks.cfg
```

### Variables

**src** - a custom kickstart file template, put it into ```{{ playbook_dir }}/templates/``` on the control host. It could be a jinja2 template or a static file but is optional. If you omit it the default template shipped with this role is used.

```yaml
src: my_kickstart_template.j2
```

**dest** - the destination path. The kickstart file will be put on the inventory host. This variable is required.

```yaml
dest: /var/www/html/ks.cfg
```

## License

GPLv3