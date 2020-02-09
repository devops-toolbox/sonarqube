Role Name
=========

sonarqube: Sonarqube

[![Build Status](https://travis-ci.org/cmihai-ansible/sonarqube.svg?branch=master)](https://travis-ci.org/cmihai-ansible/sonarqube)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.sonarqube](https://galaxy.ansible.com/devops-toolbox.sonarqube)

```bash
ansible-galaxy install devops-toolbox.sonarqube
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
sonarqube_packages_state: present
sonarqube_remove_packages: true
sonarqube_enable_service: true
sonarqube_enable_selinux: true
sonarqube_copy_templates: true
sonarqube_firewall_configure: true
sonarqube_firewall_rules:
  - service: ssh
  - port: 3389
sonarqube_users:
  - user: devops
    group: docker
sonarqube_selinux_booleans:
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
- name: Install sonarqube on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: sonarqube is configured
      import_role:
        name: devops-toolbox.sonarqube
      vars:
        sonarqube_packages_state: present
        sonarqube_remove_packages: true
        sonarqube_enable_service: true
        sonarqube_enable_selinux: true
        sonarqube_copy_templates: true
        sonarqube_firewall_configure: true
        sonarqube_firewall_rules:
          - service: ssh
          - port: 3389
        sonarqube_users:
          - user: devops
            group: docker
        sonarqube_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: sonarqube
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
