# Creating Swap Partition 
1.  Type `parted {device}`, which will bring you to interactive shell.
2.  `mkpart`, which will ask you for a name. just call it **swap**
3.  File System type should be `linux-swap`!!!
4.  Start - 1GiB
5. End - 2GiB
6. `quit`
7. `mkswap` {device name}
8.  Type `free -m`. You see the amount of swap space that is currently allocated. This does not include the swap space you have just created, as it still needs to be activated.
9.  Use `swapon {deviceName}` to switch on the newly allocated swap space. If, for instance, the swap device you have just created is /dev/sda6, use swapon /dev/sda6 to activate the swap space.
10. Add it to `/etc/fstab` to make it persistent
11.  Type free -m again. You see that the new swap space has been added to your server.