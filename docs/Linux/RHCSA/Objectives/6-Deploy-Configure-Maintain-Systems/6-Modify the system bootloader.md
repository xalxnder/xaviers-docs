The GRUB 2 boot loader makes sure that you can boot Linux.

### Runtime Parameters
Use  the `-e` command

### Persistant Parameters
To apply changes to the GRUB 2 configuration, the starting point is the `/etc/default/grub` file, which has options that tell GRUB what to do and how to do it. After writing changes, use one of the following commands:
- `grub2-mkconfig -o /boot/grub2/grub.cfg`
- `grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg`

How to know which one to use?
- Use `lsblk`, and look for `/boot`. If you see /boot/efi and /boot, you are on EFI. If you see /boot, you are on MBR