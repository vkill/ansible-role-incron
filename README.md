Ansible Role - incron
=========

[![Build Status](https://travis-ci.org/vkill/ansible-role-incron.svg?branch=master)](https://travis-ci.org/vkill/ansible-role-incron)

Incron Installation.

Requirements
------------

None.

Role Variables
--------------

TODO

Dependencies
------------

None.

Example Playbook
----------------

### with system tables

```yaml
- hosts: servers
  become: true

  roles:
    - role: vkill.incron
      incron_system_tables:
        - name: demo
          path: /home/
          mask: IN_CREATE,IN_DELETE
          command: /tmp/incron_demo.sh $# $%
```

[detailed example](vagrant_playbook.yml)

### with user tables

```yaml
- hosts: servers
  become: true

  roles:
    - role: vkill.incron
      incron_user_tables:
        - username: demo
          lines:
            - name: demo
              path: /home/demo/dir1
              mask: IN_CREATE,IN_DELETE
              command: /tmp/incron_demo.sh $# $%

            - name: demo_2
              path: /home/demo/dir2
              mask: IN_CREATE,IN_DELETE
              command: /tmp/incron_demo.sh $# $%
```

Local Testing with Vagrant
----------------

* Run vagrant

```shell
$ vagrant up --no-provision
$ vagrant provision
```

License
-------

MIT / BSD

Author Information
------------------

vkill <vkill.net@gmail.com>

&copy; 2016
