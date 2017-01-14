Reboot
======

Reboots the machine when 'Need reboot' handler is notified.

Requirements
------------

None

Role Variables
--------------

None

Dependencies
------------

None

Example Playbook
----------------

- hosts: servers
  roles:
    - reboot
  tasks:
    - debug: msg="Do reboot"
      changed_when: true
      notify: Need reboot

License
-------

MIT
