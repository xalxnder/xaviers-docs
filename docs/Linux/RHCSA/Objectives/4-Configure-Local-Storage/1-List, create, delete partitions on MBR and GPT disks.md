Always start with `lsblk` just to get an overview.
![[Pasted image 20220902050824.png]]

# MBR
Create 
fdisk {device}
1. fdisk /dev/{deviceName}
2. `n` - To create a new partition
3. `p` - To create a primary partition
4. It will ask for first sector. You can just hit enter.
5. It will now as for Last Sector. Type the value of how big you want your partition to be.
6. `w` - To write/save your changes.

# GPT
Create
gdisk {device}
1. `parted /dev/{deviceName}`
2. `mklabel gpt`
3. Verify with `print`
4. `mkpart one 1MiB 1024MiB`
5. quit
6. `udevadm settle`

>[!WARNING] For parted there is a difference between G and GiB
