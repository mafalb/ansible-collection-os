# An ansible role for provisioning Operating systems to bare metal hardware [![Build Status](https://travis-ci.com/mafalb/ansible-provision.svg?branch=master)](https://travis-ci.com/mafalb/ansible-provision)

## Basic Usage

```
- hosts: localhost
  roles:
    - role: kickstart
      dest: /var/www/html/ks.cfg
``` 

## Variables

**src** - the path of the source of the kickstart file, relative to the `{{ playbook_dir }}`, located on the control host. It could be a jinja2 template or a static file but is optional. If you omit it the default template shipped with this role is used.
```
src: "templates/my_kickstart_template.j2"
```

**dest** - the destination for the provision file, e.g.
```
dest: /var/www/html/ks.cfg
```

## kickstart data

```
ks:
  fqdn: srv01.example.com
  user: ansible
  disks:
    - sda
```
  
```
ks.fqdn ansible_fqdn
```

