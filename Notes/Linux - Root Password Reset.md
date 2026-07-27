---
tags:
  - Linux
  - VMware
---
# Prep
## VMware 

Resetting the root password requires access to the grub menu at boot, ensure there is a boot delay so you have the opportunity to get there:

1. Go into VMWare VM Settings, VM Options, Boot Options Set Boot Delay to 10000 Click Ok
2. Open the remote console to VM
3. Restart the VM

> Do not forget to revert any changes made after successfully resetting the root password
# Reset Root Password

## Fedora / Red Hat / CentOS / Rocky

> See [How to reset the root password on RHEL 7 and CentOS 7](https://www.youtube.com/watch?v=UvgfIL1yPa8)

The following applies to the Fedora family of Linux distros:

1. In Linux Grub menu, select the top entry and click the `e` key
2. In the UI navigate down to the line that starts with `linux16`
3. Press the `End` key to move to the end of the line
4. Add a single whitespace character
5. Input `rd.break` after the whitespace
6. Input CTRL + X to save and boot into shell as root _(This isn't really "saved" and will reset after reboot)_
7. Execute the `mount` command in the shell to list system volumes as needed
8. Execute `mount –o remount,rw /sysroot/` to mount `/sysroot/` to your context with read/write permissions
9. Execute `chroot /sysroot/` to set the mounted `/sysroot/` as the default root directory for your shell context
10. Execute `passwd` to initiate password for your login, which should be the root account
11. Input the desired root password
12. Execute `touch /.autorelabel` to avoid issues with SELinux
13. Execute `exit` as many times as it takes until the server reboots