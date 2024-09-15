Task 01: Using the nmcli command, configure a network connection on the primary network device with IP address 192.168.0.242/24, gateway 192.168.0.1, and nameserver 192.168.0.1. 
Use different IP assignments based on your lab environment. (Exercise 16-

Task 02: Using the hostnamectl command, set the system hostname to rhcsa2.example.com and alias rhcsa2. Make sure that the new hostname is reflected in the command prompt. (Exercises 16-1 and 16-5).  

Task 03: Create a user account called bob with UID 7000 and comments “I am bob”. Set the maximum allowable inactivity for this user to 30 days. (Exercises 5-2, and 6-1 or 6-2). 

Task 04: Create a user account called tedd with a non-interactive shell. (Exercise 5-4). 

Task 05: Create a file called testfile1 under /var/tmp with ownership and owning group set to root. Configure access ACLs on the file and give lisa read and write access. Test access by logging in as lisa and editing the file. (Chapter 03, topic: Creating Files and Directories, and Exercise 4-7).  


Task 07: Create a logical volume called lv1 of size equal to 10 LEs in vg1 volume group (create vg1 with PE size 8MB in a partition on the 400MB disk). Initialize the logical volume with XFS type and mount it on /mnt/lvfs1. Create a file called lv1file1 in the mount point. Set the file system to automatically mount at each system reboot. 

Task 08: Add a group called sres and change group membership on /mnt/ lvfs1 to sres. Set read/write/execute permissions on /mnt/lvfs1 for the owner, group members, and others. 

Task 09: Extend the file system in the logical volume lv1 by 64MB without un- mounting it and without losing any data. Confirm the new size for the logical volume and the file system. (Exercise 15-4).  

Task 10: Create a swap partition of size 85MB on the 400MB disk. Use its UUID and ensure it is activated after every system reboot. (Exercise 15-6).  

Task 11: Create a disk partition of size 100MB on the 400MB disk and format it with Ext4 file system structures. Assign label stdlabel to the file system. Mount the file system on /mnt/stdfs1 persistently using the label. Create file stdfile1 in the mount point. (Exercise 13-2 or 13-4, Chapter 15, topic: Labeling a File Sys- tem, and Exercise 15-1). 


Task 12: Use the tar and gzip command combination to create a compressed archive of the /etc directory. Store the archive under /var/tmp using a filename of your choice. (Exercise 3-1).  

Task 13: Create a directory /direct01 and apply SELinux contexts for /root to it. (Exercise 21-2).  

Task 14: Set up a cron job for bob to search for files by the name “core” in the /var directory and copy them to the directory `/var/tmp/coredir1`. This job should run every Monday at 1:20 a.m. (Chapter 04, topics: Using the find Command, and Using find with -exec and -ok Flags, and Exercise 8-4).  

Task 15: Search for all files in the entire directory structure that have been modified in the past 30 days and save the file listing in the /var/tmp/ mod-files.txt file. (Chapter 04, topics: Using the find Command and Using find with -exec and -ok Flags).  

Task 16: Modify the bootloader program and set the default autoboot timer value to 2 seconds. (Exercise 11-1).  

Task 17: Determine the recommended tuning profile for the system and apply it. (Exercise 12-2).  

Task 18: Configure Chrony to synchronize system time with the hardware clock. Remove all other NTP sources. (Exercise 18-1).  

Task 19: Install package group called “Development Tools” and capture its information in /var/tmp/systemtools.out file. (Chapter 03, topic: Regular Ex- pressions, and Exercise 10-3). 

Task 20: Lock user account bob. Use regular expressions to capture the line that shows the lock and store the output in file /var/tmp/bob.lock. (Chapter 03, topic: Regular Expressions, and Exercise 6-3). 

Task 21: Write a bash shell script so that it prints RHCSA when RHCE is passed as an argument, and vice versa. If no argument is provided, the script should print a usage message and quit with exit value 5. (Chapter 22: Script10).  

Task 22: Launch a root container and configure it to auto-start via systemd. (Exercise 23-9).  

Task 23: Launch a container as user80 with /data01 mapped to /data01 using the latest version of the ubi8 image. Configure a systemd service to auto-start the container on system reboots without the need for user80 to log in. Create files under the shared mount point and validate data persistence. (Exercise 23-7 and 23-10).