# Creating Logical Volumes
Creating logical volumes involves creating 3 layers in the LVM architecture:
1. Convert physical devices into physical volumes
2. Create the volume group and assign PVs to it.
3. Create the logical volume itself. 
>[!TIP] For the exam, you must memorize pv, vg, and lv. Remember though, use tab to see their options. 


### Create The Partition
1. `parted /dev/{deviceName}`
2. It will ask for a partition table
	1. msdos or gpt
![[Pasted image 20220902124750.png]]
3. `mkpart`
4. It will ask for a partition name:
	1. Set it to `lvm1`
5. File System Type
	1. Just press `enter`
6. Set the start point
7. Set the end point
8. Verify with `print`
9. From the print command, get the number of the partition and type `set {number} lvm on`
10. `quit`
![[Pasted image 20220902124832.png]]
### Create The Physical Volume
1. `pvcreate /dev/{partition}`
	1. You should receive a success message
![[Pasted image 20220902124439.png]]

### Create The Volume Group
1. `vgcreate vgdata /dev/{partition}`
	1. Again, you should receive a success message
![[Pasted image 20220902124506.png]]

### Create The Logical Volume
1. `lvcreate -n lvdata -L 812M vgdata`
![[Pasted image 20220902124540.png]]
### Putting Filesystem on the Logical Volume
1. mkfs.xfs /dev/vgdata/lvdata 
![[Pasted image 20220902124614.png]]
### Mount it in FSTAB
1. Create your mount point
	1. mkdir /mounts/lvm1
2. vim /etc/fstab
	1. ![[Pasted image 20220902055615.png]]
3. mount -a
4. Reboot!
