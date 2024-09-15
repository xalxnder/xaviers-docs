1.  Create a user named **tom**, this user shall have a user id of 777 and a nologin shell.
2.  Create five users: **student, jerry, laura, mary and scott** with home directories in /home.

3.  Set their passwords to **RHCSA123$**

4.  Make accounts for **mary and scott** to expire on December 31, 2030
	1. Verify with `chage -l $username`

5.  Users **jerry and laura** should have their secondary groups set to the group **database** (Create the group if it doesn’t exist).

6.  Add a group called **developers** and change the group ownership on /mnt/mobile to the group developers.
  
7.  Set read/write/execute permissions on the directory /mnt/mobile to the owner and group members and no permissions for others.

8.  Create a Directory called **dir2** as a user **laura** in her home directory and set default ACLs (Access Control List) on it for user **mary** for read and write access.
  
9.  Modify the boot loader configuration and set the default autoboot timer value to 2 seconds.
	1. Save changes with `grub2-mkconfig -o /boot/grub2/grub.cfg`
  
10.  Configure your firewall to accept all ftp traffic to the system.

11.  Give user tom sudo access (with no password prompts) to the following tools:
	1. yum.
	2. firewall-cmd
     
12.  Start Firewalld and make sure it starts automatically on boot.

13.  Create a volume group named vg_apps using the two disks /dev/sdb and /dev/sdc.
  
14.  Create a logical volume named lv_mobile with size of 7GB with mount point /mnt/mobile (create the mount point as well) formatted with xfs file system structure and a block size of **100MB**.
	1. Create a file named pixel.txt in the mount point and Set the file system to automatically mount at each system reboot.
  
16.  Create a swap partition of size **100MB** on the disk /dev/sdd. Use its UUID and ensure it is activated after every system reboot. Make sure the swap partition is enabled as well.

17.  Create a standard partition of size **100MB** on any available disk and format it with the ext4 file system structure.
	1. Mount the file system on /mnt/ext4 (create the mount point if it doesn’t exist) persistently using a LABEL=STANDARD. Also create a file called docker.txt in the mount point.

19.  Create a temporary directory named /run/hello and create temporary file inside /run/hello named temp1.txt
   
20.  Add a host **172.16.1.101** with an alias RHCSA.

21.  Create a new network connection “myhome-connection” with the following ( **ip address 192.168.0.1/24  - gateway 192.168.0.254  -  DNS 192.168.0.254** ).

23.  Using only the tar command, create a compressed archive using xz compression method of the /etc/yum.repos.d directory. Name the files repos.tar.xz and store the file in directory /root/compressed (create compressed if it’s not there already).

24.  Install nfs server-2. Create the directory /media/nfs and Permanently mount the NFS-SHARE on server-1 on /media/nfs
   
25.  Let’s assume there is an NFS share on 192.168.100.113 with the name of NFS_SHARE. Mount the NFS_SHARE on /files/mynfs on demand with a timeout of 10 seconds.
#practice-exam 



