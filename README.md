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

### Basic Usage

```ansible
- hosts: localhost
  roles:
    - role: mafalb.os.kickstart
      dest: /var/www/html/ks.cfg
```

### Variables

**src** - the path of the source of the kickstart file, relative to the `{{ playbook_dir }}`, located on the control host. It could be a jinja2 template or a static file but is optional. If you omit it the default template shipped with this role is used.

```yaml
src: my_kickstart_template.j2
```

**dest** - the destination for the provision file

```yaml
dest: /var/www/html/ks.cfg
```


