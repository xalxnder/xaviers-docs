
2.  Create user student with password password, and user root with password password.
4.  Create a 500-MiB partition on your second hard disk, and format it with the Ext4 file system. Mount it persistently on the directory /mydata, using the label mydata.
5.  Set default values for new users. A user should get a warning three days before expiration of the current password. Also, new passwords should have a maximum lifetime of 120 days.
6.  Create users edwin and santos and make them members of the group `livingopensource` as a secondary group membership. Also, create users serene and alex and make them members of the group operations as a secondary group.
7.  Create shared group directories` /groups/livingopensource` and `/groups /operations`, and make sure the groups meet the following requirements
    -   Members of the group `livingopensource` have full access to their directory.
    -   Members of the group operations have full access to their directory.
    -   Others has no access to any of the directories.
    -   Alex is general manager, so user `alex` has read access to all files in both directories and has permissions to delete all files that are created in both directories. 
	    - Just make Alex the own of the `operations` and `livingopensource` directories
1.  Create a 1-GiB swap partition and mount it persistently.
2.  Find all files that have the SUID permission set, and write the result to the file /root/suidfiles.
	1. `find / -perm /2000`
3.  Create a 1-GiB LVM volume group. In this volume group, create a 512-MiB swap volume and mount it persistently.
4.  Install a web server and configure it to listen on port 8080.
5.  Create a configuration that allows user edwin to run all administrative commands using sudo.