PI LCD setup
============

Configures Pi for Waveshare 10.1inch HDMI LCD screen.
http://www.waveshare.com/wiki/10.1inch_HDMI_LCD

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

- Triggers 'Need reboot' handler from role 'reboot'

Example Playbook
----------------

    - hosts: servers
      roles:
         - lcd

License
-------

MIT
