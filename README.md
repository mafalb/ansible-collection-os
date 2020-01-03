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