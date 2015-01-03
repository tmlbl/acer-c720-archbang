acer-c720-archbang
==================

## About this repo
I use a script I wrote called [dotman](http://github.com/tmlbl/dotman) to manage these config files. It is not perfect but I find it quite useful. You can read the .dotman file in this repository to get an idea of where the files are actually located on the ArchBang base system.

These are my personal config files so no effort has been made to keep them generic. However, together they constitute a very usable system which I recommend trying. If you want to use dotman, you can change every instance of /home/tim in the .dotman file to match your own home directory, or run this command:

`sed -i "s/\/home\/tim/$(echo $HOME | sed 's/\//\\\//g')/g" .dotman`

Then by running `dotman export [file]` you can copy these configs to their intended paths.

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
