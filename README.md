acer-c720-archbang
==================

## Installation
I installed by creating a pen drive on Windows using Universal USB Installer. In order to get the live CD to boot, I added `mem=1536m` to the boot command, and changed the archiso parameter from `ARCHBANG` to `UUI`. From there I ran the install script as normal.

## Fixing suspend and resume
Followed instructions from [Arch Wiki](https://wiki.archlinux.org/index.php/Chromebook#Fixing_suspend)
Added this line to `/etc/default/grub`:
`GRUB_CMDLINE_LINUX_DEFAULT="tpm_tis.interrupts=0 modprobe.blacklist=ehci_pci"`
Then ran `sudo grub-mkconfig -o /boot/grub/grub.cfg`
Then reboot.

## Improving the touchpad performance
I edited `/etc/X11/xorg.conf.d/10-synaptics.conf`. The edited file is in this repository. I turned off tap to click because I kept triggering it accidentally.
