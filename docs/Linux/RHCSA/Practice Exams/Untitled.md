
### Understand and use essential tools

-   _**Task 1 :**_  
    Find all setuid files on the system and save the list
	    find / -perm 2000 > list.txt
    
-   _**Task 2 :**_  
    Find all log messages in /var/log/messages that contain "ACPI", and export them to a file called /root/logs. Then archive all of /var/log and save it to /tmp/log_archive.tgz
	    **grep ACPI /var/log/messages > /root/logs**
	    **tar -czvf /tmp/log_archive.tgz /var/log**
    
-   _**Task 3 :**_  
    Create tar files compressed with gzip and bzip2 of /home and extract them
	    Gzip:
	    tar -cfz home.tar.gz /home
	    tar -xfz home.tar.gz
	    BZip2
	    tar -cfj home.tar.bz2 /home
	    tar -xfj home.tar.bz2
	    
    
-   _**Task 4 :**_  
    Create an empty file hard1 under /tmp and display its attributes. Create hard links hard2 and hard3. Edit hard2 and observe the attributes. Remove hard1 and hard3 and list the attributes again
		- cd /tmp 
		- touch /tmp/hard1
		- ln hard1 hard2 
		- vim hard2
		- ls -li hard 2
		- 

    
_**Task 5 :**_  
- Create an empty file soft1 under /root pointing to /tmp/hard2. Edit soft1 and list the attributes after editing. Remove hard2 and then list soft1
	- ln -s /tmp/hard2 soft1
	- ls -li soft1

_**Task 6 :**_  
- Create a file `perm_file1` with read permissions for owner, group and other. 
	- touch perm_file1
	- chmod 444 perm_file1
- Add an execute bit for the owner and a write bit for group and public. 
	- chmod u+x, g+w, o +w
- Revoke the write bit from public and assign read, write, and execute bits to the three user categories at the same time. 
	- chmod o - w
	- chmod 777
	- You can also use `a`, to assign permissions to all users!
- Revoke write from the owning group and revoke write and execute bits from public
	- chmod g-w, o-w, o-x `perm_file1`


### Create simple shell scripts

-   _**Task 1 :**_  
    Create a bash script that display the hostname ,system information and the users that are currently logged in
    
-   _**Task 2 :**_  
    Create a bash script that shows total count of the supplied arguments , value of the first argument, PID of the script and all the supplied arguments
    
-   _**Task 3 :**_  
    Create a bash script that can create user10, user20 and user30 accounts with each account is create a message saying " The account is created successfuly " will be displayed otherwise the script will terminate . In case of a successful account creation assign the user account a password as their username
    
-   _**Task 4:**_  
    Write a script that finds all the files owned by new_user and have size greater than 30KB and less than 50KB and store them in /tmp/
    
-   _**Task 5 :**_  
    Write a script named backup.sh under /root which will search files less than 2M from /usr and store it in /root/backup
    
-   _**Task 6 :**_  
    As a System Administrator you are responsible to take a backup of your /etc directory every night. Build a shell script to take a backup of the /etc/directory using the tar command. The backup script should be named as /root/backup.sh. Schedule this script to run at 11:00 PM every night – except Sundays.
    

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#operate-running-systems)Operate running systems

_**Task 1 :**_  
- Modify the GRUB timeout and make it 1 second instead of 5 seconds  
	- `vim /etc/default/grub`
	- `grub2-mkconfig /boot/grub2/grub.cfg`
	- To determin if the system is booted in BIOS or UEFI:
		- `dmesg | egrep -i "efi|bios"`

_**Task 2 :**_  
- Terminate the boot process at an early stage to access a debug shell to reset the root password
	- reboot now
	- ctrl+e

_**Task 3 :**_  
    Download the latest available kernel packages from the Red Hat Customer Portal and install them
    
_**Task 4 :**_  
- Install the tuned service, start it and enable it for auto-restart upon reboot. 
	- `dnf install tuned`
	- `systemctl enable --now tuned`
- Display all available profiles and the current active profile. 
	- `tuned-adm list`
	- `tuned-adm active`
- Switch to one of the available profiles and confirm.
	-  `tuned-adm profile balanced``
	- ` tuned-adm acticve`
- Determine the recommended profile for the system and switch to it. 
	- `tuned-adm recommend`
	- `tuned-adm profile virtual-guest`
- Deactivate tuning and reactivate it
	- `tuned-adm off`
	- `tuned-adm profile virtual-guest`

_**Task 5:**_  
- Launch the command `dd if=/dev/zero of=/dev/null` three times as a background job. 
- Increase the priority of one of these.
	- renice -n -10
- Change the priority of the same process again, but this time use the value -15. Observe the difference.
	- renice -n -15
- Kill all the dd processes you just started
	- pkill dd

_**Task 6 :**_  
- Configure the journal to be persistent across system reboots. 
	- In /etc/systemd/journald.conf, ensure that Storage is set to auto.
	- mkdir -p /var/log/journal
	- reboot
- Configure logrotate to keep ten old versions of log files
	- vim /etc/logrotate.conf
		- rotate 10

_**Task 7:**_  
- Copy the /etc/hosts file to the /tmp directory on server2 using scp command. 
	- `scp /etc/hosts server2:/tmp`
- Try to connect to server2 as user root and copy the /etc/passwd file to you home directory

_**Task 8 :**_  
- Download and install the apache web service. 
- Try to configure apache to log error messages through syslog using the facility local1.
- Create a rule that send all messages that it receives from local1 (That used above) facility to /var/log/httpd-error.log  verify the last changed by accessing a page that does not exist

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#configure-local-storage)Configure local storage

_**Task 1 :**_  
- Create a 2 GB gpt partition and format the partition with xfs and mount the device persistently
	```bash
	 lsblk		=> to list all the block device
	 fdisk /dev/sdb
	 press m   => list all the opts
	 enter g   => to create a new gpt part 
	 enter n   => to add new part 
	 accept the default part
	 accept the default starting sector
	 For the ending sector , Enter +2G 
	 enter w   => to write table to disk and exit 
	 partprobe => to inform the os part table change  
	 mkfs.xfs /dev/sdb1 
	 blkid   => to grep the uuid 
	 mkdir /mnt/task1
	 echo 'UUID=xxxx /mnt/task1 xfs defaults 0 0' >> /etc/fstab
	 mount -a 
	```
_**Task 2 :**_ 
- Assign partition type "msdos" to /dev/sdc for using it as an MBR disk. Create and confirm a 100MB primary partition on the disk

    ```bash
    same steps created in task 1 expet the size and the type "msdos" 
	  # enter o   => to create an MBR disk 
    ```


_**Task 3 :**_  
- Delete the sdb1 partition that was created in Task1 above   
	- When deleting a partition, make sure you UMOUNT
	```bash
	umount /mnt/test
	Add comment to fstab
	fdisk {device}
	d
	```

_**Task 4 :**_  
- Initialize one partition sdb1 (90MB) and one disk sdc (250MB) for use in LVM. 
- Create a volume group called vgbook and add both physical volumes to it. 
- Use the PE size of 16MB and list and display the volume group and the physical volumes

 _**Task 5:**_  
 - Create two logical volumes, lvol1 and lvbook1, in the vgbook volume group. 
 - Use 120MB for lvol1 and 192MB for lvbook1. 
 - Display the details of the volume group and the logical volumes

_**Task 6 :**_ 
- Add another partition sdb2 of size 158MB to vgbook to increase the pool of allocatable space.
- Initialize the new partition prior to adding it to the volume group. 
- Increase the size of lvbook1 to 336MB. Display the basic information for the physical volumes, volume group, and logical volume

_**Task 7 :**_  
- Rename lvol0 to lvbook2. 
- Decrease the size of lvbook2 to 50MB using the `lvreduce` command and then add 32MB with the `lvresize` command. 
- Remove both logical volumes. 
- Display the summary for the volume groups, logical volumes, and physical volumes

_**Task 8 :**_  
- Uninitialize all three physical volumes - sdb1, sdb2, and sdb - by deleting the LVM structural information from them. 
- Use the pvs command for confirmation.
- Remove the partitions from the sdd disk and verify that all disks are now in their original raw state

_**Task 9 :**_  
-  Create a new logical volume (LV-A) with a size of 30 extents that belongs to the volume group VG-A (with a PE size of 32M). After creating the volume, configure the server to mount it persistently on /mnt

_**Task 10 :**_  
-  Create 1 swap area in a new 40MB partition called sdc3 using the mkswap command.
- Create another swap area in a 140MB logical volume called swapvol in vgfs. 
- Add their entries to the `/etc/fstab` file for persistence. 
- Use the UUID and priority 1 for the partition swap and the device file and priority 2 for the logical volume swap. Activate them and use appropriate tools to validate the activation
    

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#create-and-configure-file-systems-)Create and configure file systems  

 _**Task 1 :**_  
 - Create 2x100MB partitions on the /dev/sdb disk, initialize them separately with the Ext4 and XFS file system types
 - Create mount points called` /ext4fs` and `/xfs1`
 - Attach them to the directory structure, verify their availability and usage
 - Mount them persistently using their UUIDS

_**Task 2 :**_  
- Create a volume group called vgfs comprised of a 160MB physical volume created in a partition on the /dev/sdb disk. 
- The PE size for the volume group should be set at 16MB. 
- Create 2 logical volumes called ext4vol and xfsvol of size 80MB each and initialise them with the Ext4 and XFS file system types. 
- Ensure that both file systems are persistently defined using their logical volume device filenames.
- Create mount points /ext4fs2 and /xfsfs2, mount the file systems, and verify their availability and usage

_**Task 3 :**_  
- Grow the size of the vgfs volume group that was created above by adding another disk to it. Extend the ext4vol logical volume along with the file system it contains by 40MB

_**Task 4 :**_  
 - Create a directory called /common and export it to server in read/write mode. Ensure that NFS traffic is allowed through the firewall. Confirm the export

_**Task 5 :**_  
- Mount the /common that exported in task 4 . Create a mount point called /local. Add the remote share to the file system table for persistence. Create a test file in the mount point and confirm the file creation on the NFS server

_**Task 6 :**_  
Create users jeff, jack and group sgrp with GID 9999. add jeff and jack to this group. Create a directory /sdir with ownership and owning groups belong to root and sgrp, and set the setgid bit on /sdir

_**Task 7:**_  
- Create a file under /tmp as jeff and try to delete it as jack. Unset the sticky bit on /tmp and try to erase the file again. Restore the sticky bit on /tmp

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#automount)Automount

_**Task 1 :**_  
- Configure a direct map to automount the NFS share `/common` that is available from server2. 
- Install the relevant software, create a local mount point /autodir, and set up AutoFS maps to support the automatic mounting. 
- Note that /common is already mounted on the /local mount point on server1 via fstab. Ensure there is no conflict in configuration or functionality between the 2
    
_**Task 2:**_  
- On server1 (NFS server), create a user account called user30 with UID 3000. Add the /home directory to the list of NFS shares so that it becomes available for remote mount. 
- On server2 (NFS client), create a user account called user30 with UID 3000, base directory /nfshome, and no user home directory. 
- Establish an indirect map to automount the remote home directory of user30 under /nfshome. Observe that the home directory of user30 is automounted under /nfshome when you sign in as user30
    
-   _**Task 3 :**_  
    Configura Autofs
    
    -   All Ldapuser2 home directory is exported via NFS, which is available on classroom.example.com (172.25.254.254) and your NFS-exports directory is **/home/guests/Ldapuser2**,
    -   Ldapuser2's home directory is classroom.example.com:/home/guests/ldapuse2
    -   Ldapuser2's home directory should be automount autofs service.
    -   Home directories must be writable by their users. while you are able to log in as any of the user ldapuser1 through ldapuser20, the only home directory that is accessible from your system is ldapsuser2


### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#deploy-configure-and-maintain-systems)Deploy configure and maintain systems

-   _**Task 1 :**_  
    As Bob, create a once-off job that creates a file called /testresults/Hello.sh containing the text "Hello World. This is Admin." in 2 days later
    
-   _**Task 2:**_  
    Set the system time zone and configure the system to use NTP
    
-   _**Task 3 :**_  
    Create a periodic job that appends the current date to the file ~/tracking every 5 minutes every Sunday and Wednesday between the hours of 3am and 4am. Remove the ability of bob to create cron jobs
    
-   _**Task 4 :**_  
    Create a daily cron job at 4:27PM for the Derek user that runs cat /etc/redhat-release and redirects the output to /home/derek/release
    
-   _**Task 5 :**_  
    Submit a job as jeff to run the date command at 11:30pm on March 31, 2022, and have the output and any error messages generated redirected to /tmp/date.out. List the submitted job and then remove it
    
-   _**Task 6 :**_  
    Access the repositories that are available on the RHEL 8 image. Create a definition file for the repositories and confirm
    
-   _**Task 7 :**_  
    Verify the integrity and authenticity of a package called dcraw located in the /mnt/AppStream/Packages directory on the installation image and then install it. Display basic information about the package, show files it contains, list documentation files, verify the package attributes and remove the package
    
-   _**Task 8 :**_  
    Determine if the cifs-utils package is installed and if it is available for installation. Display its information before installing it. Install the package and display its information again. Remove the package along with its dependencies and confirm the removal
    
-   _**Task 9 :**_  
    Perform management operations on a package group called system tools. Determine if this group is already installed and if it is available for installation. List the packages it contains and install it. Remove the group along with its dependencies and confirm the removal
    
-   _**Task 10 :**_  
    Perform management operations on a module called postgresql. Determine if this module is already installed and if it is available for installation. Show its information and install the default profile for stream 10. Remove the module profile along with any dependencies and confirm its removal
    

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#manage-basic-networking)Manage basic networking

-   _**Task 1 :**_  
    Create a connection profile for the new network interface on server using a text editing tool. Assign the IP 172.10.10.110/24 with gateway 172.10.10.1 and set it to autoactivate at system reboots. Deactivate and reactive this interface at the command prompt
    
-   _**Task 2 :**_  
    Create a connection profile using the nmcli command for the new network interface that was added to server2. Assign the IP 172.10.10.120/24 with gateway 172.10.10.1, and set it to autoactivate at system reboot. Deactivate and reactivate this interface at the command prompt
    
-   _**Task 3 :**_  
    Update the /etc/hosts file on both server1 and server2. Add the IP addresses assigned to both connections and map them to hostnames . Test connectivity from server to client and from client to server using their IP addresses and then their hostnames
    
-   _**Task 4 :**_  
    Determine the current active zone. Add and activate a permanent rule to allow HTTP traffic on port 80, and then add a runtime rule for traffic intended for TCP port 443. Add a permanent rule to the internal zone for TCP port range 5901 to 5910. Confirm the changes and display the contents of the affected zone files. Switch the default zone to the internal zone and activate it
    
-   _**Task 5 :**_  
    Remove the 2 permanent rules added above. Switch back to the public zone as the default zone, and confirm the changes
    
-   _**Task 6 :**_  
    Set the system hostname to server1.example.com and alias server1. Make sure that the new hostname is reflected in the command prompt
    

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#manage-users-and-groups)Manage users and groups

-   _**Task 1 :**_  
    Create three users (Derek, Tom, and Kenny) that belong to the instructors group. Prevent Tom's user from accessing a shell, and make his account expire 10 day from now
    
-   _**Task 2 :**_  
    Add 3 new users alice, bob and charles. Create a marketing group and add these users to the group. Create a directory /marketing and change the owner to alice and group to marketing. Set permissions so that members of the marketing group can share documents in the directory but nobody else can see them. Give charles read-only permission. Create an empty file in the directory
    
-   _**Task 3 :**_  
    Create bill with the default attributes in the useradd and login.defs files. Assign this user a password and show the line entries from all 4 authentication files
    
-   _**Task 4 :**_  
    For jack change the login name to jacknew, UID to 2000, home directory to /home/jacknew, and login shell to /sbin/nologin. Display the line entry for user2new from the passwd for validation. Remove this user and confirm the deletion
    
-   _**Task 5 :**_  
    Configure password aging for Derek using the chage command . Set the mindays to 7, maxdays to 28, and warndays to 5. Verify the new settings. Rerun the command and set account expiry to January 31, 2022
    
-   _**Task 6 :**_  
    Configure password aging for using the PASSWD command. Set the mindays to 10, maxdays to 90, and warndays to 14, and verify the new settings. Set the number of inactivity days to 5 and ensure that the user is forced to change their password upon next login
    
-   _**Task 7 :**_  
    
    Create a group called linuxadm with GID 5000 and another group called dba sharing the GID 5000. Add Derek as a secondary member to group linuxadm
    
-   _**Task 8 :**_  
    Change the linuxadm group name to sysadm and the GID to 6000. Modify the primary group for Derek to sysadm. Remove the sysadm group and confirm
    

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#manage-security)Manage security

-   _**Task 1 :**_  
    Create a file acluser as jeff in /tmp and check if there are any ACL settings on the file. Apply access ACLs on the file for jeff for read and write access. Add jack to the file for full permissions. Remove all access ACLs from the file
    
-   _**Task 2 :**_  
    Generate a password-less ssh key pair using RSA for jeff on server. Distribute the public key to client and attempt to log on to client from server. Show the log file message for the login attempt
    
-   _**Task 3 :**_  
    Remove the sshd service rule from the runtime configuration on server and try to access the server from the client using the ssh command
    
-   _**Task 4:**_  
    Create a directory sedir1 under /tmp and a file sefile1 under sedir1. Check the context on the directory and file. Change the SELinux user and type to user_u and public_content_t on both and verify
    
-   _**Task 5 :**_  
    Add the current context on sedir1 to the SELinux policy database to ensure a relabeling will not reset it to its previous value. Next, you will change the context on the directory to some random values. Restore the default context from the policy database back to the directory recursively
    
    tip: chcon write the context to the file sys and not to the policy so everything is overwritten when the fs is relabeled where the original context is restored from the policy to the file sys so it's recommended to work with semanage
    
-   _**Task 6 :**_  
    Add a non-standard port 8010 to the SELinux policy database for the httpd service and confirm the addition. Remove the port from the policy and verify the deletion
    
-   _**Task 7 :**_  
    Create a file called sefile2 under /tmp and display its context. Copy this file to the /etc/default directory, and observe the change in the context. Remove sefile2 from /etc/default, and copy it again to the same destination, ensuring that the target file receives the source file's context
    
-   _**Task 8 :**_  
    Display the current state of the Boolean nfs_export_all_rw. Toggle its value temporarily, and reboot the system. Flip its value persistently after the system has been back up
    

### [](https://github.com/soficx/rhcsa/tree/master/Only%20Questions#manage-containers)Manage containers

_**Task 1 :**_  
- Download the Apache web server container image (httpd 2.4) and inspect the container image. 
- Check the exposed ports in the container image configuration


_**Task 2 :**_  
- Run the httpd container in the background. 
- Assign the name myweb to the container, verify that the container is running, stop the container and verify that it has stopped, and delete the container and the container image

 _**Task 3 :**_ 
 - Pull the Apache web server container image (httpd 2.4) and run the container with the name webserver. 
 - Configure webserver to display content "Welcome to container-based web server". 
 - Use port 3333 on the host machine to receive http requests. Start a bash shell in the container to verify the configuration
 -
 _**Task 4 :**_
 - Configure the system to start the webserver container at boot as a systemd service. 
 - Start/enable the systemd service to make sure the container will start at boot, and reboot the system to verify if the container is running as expected


_**Task 5 :**_  
- Create a container logserver from an image rsyslog in server1 from registry.redhat.io  
-   Configure the container with systemd services by an existing user user10.  
-   Service name should be container-logserver, and configure it to start automatically across reboot.  
-   Configure your host journal to store all journal across reboot, copy all *.journal from /var/log/journal and all subdirectories to /home/user10/container_logserver  
-   Configure automount `/var/log/journal` from logserver (container) to /home/user10/container_logserver when container starts.

