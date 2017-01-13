PI LCD Detup
============

Configures Pi for LCD panel.

Requirements
------------

None

Role Variables
--------------

- lcd_max_usb_current
- lcd_hdmi_group
- lcd_hdmi_mode
- lcd_hdmi_cvt
- lcd_display_rotate

See LCD panel manual.

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - lcd

License
-------

MIT
