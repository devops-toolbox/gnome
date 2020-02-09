Role Name
=========

gnome: Gnome

[![Build Status](https://travis-ci.org/cmihai-ansible/gnome.svg?branch=master)](https://travis-ci.org/cmihai-ansible/gnome)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.gnome](https://galaxy.ansible.com/devopstoolbox.gnome)

```bash
ansible-galaxy install devopstoolbox.gnome
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
gnome_packages_state: present
gnome_remove_packages: true
gnome_enable_service: true
gnome_enable_selinux: true
gnome_copy_templates: true
gnome_firewall_configure: true
gnome_firewall_rules:
  - service: ssh
  - port: 3389
gnome_users:
  - user: devops
    group: docker
gnome_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install gnome on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: gnome is configured
      import_role:
        name: devopstoolbox.gnome
      vars:
        gnome_packages_state: present
        gnome_remove_packages: true
        gnome_enable_service: true
        gnome_enable_selinux: true
        gnome_copy_templates: true
        gnome_firewall_configure: true
        gnome_firewall_rules:
          - service: ssh
          - port: 3389
        gnome_users:
          - user: devops
            group: docker
        gnome_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: gnome
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)
