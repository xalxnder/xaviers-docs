1.  Create three users jerry, kobe, and lebron. All three users must change their password upon their first login.
	1. passwd -e
  
2.  Create a group named nba and jerry, kobe, and lebron to it. All members of the nba group should have access to install any package on the system.
 
3.  Create a directory named ` /staples ` and make lebron the owner of this directory.
	1. All the three members of the nba group should have full permissions to the ` /staples ` directory.
  
4.  Create a new file named `champion.txt` in ` /staples `.
  
5.  kobe should be the owner of the file champion.txt and lebron should have read access to the champion.txt file.
  
6.  The champion.txt file should NOT be modified or deleted by any user on the system.
  
7.  Create a soft link to your tmp directory called mytemp in var. Also create a hard link in `/root `to ` /etc/services `  , and name it ports.txt .
  
8.  Create a file named file1 in ` /root ` and make sure this file can’t be deleted. Furthermore, give jerry read access to file1.
 
9.  Create a new user Mary, with a nologin shell. Make a copy of the file ` /etc/passwd ‘ called ‘ /root/passwd.bk ` and allow Mary to read and write to the file ` /root/passwd.bk `
 
10.  Find all the file names under ` /etc ` that begins with letter v and ends with .conf
 
11.  As the root user, create a crontab entry that runs every 2 minutes to update the timestamp of the ` /etc/passwd ‘ file.
 
12.  Set up a cron job as jerry user to search for log files in the ` /var ` directory and list them in ` /var/log/logfiles `. This job should run every Monday at 1:20 am system time.
	1. ls -lR | grep \*.log
 
13.  Permanently disable SELinux on your system and change your default target to multi-user target.
  
14.  The virtual machine should have an IP address of 192.168.100.113. You should configure 8.8.8.8 as the DNS server.
  
15.  Install and configure Apache web server. Change the Apache default directory to ` /web/html ` and make sure it works. Apache service should start automatically upon server reboots.
 
16.  Create a volume group named myvg that spans two of your three available secondary disks.
  
17.  Create two logical volumes named mylv1 and mylv2 with a size of 500MB for each one of them.
 
18.  Create an ext4 filesystem on the mylv1 logical volume and mount it permanently on the ` /myfiles ` directory with the label FILES.
  
19.  Extend the logical volume mylv2 to 500MB.
 
20.  Create a 1 GB swap partition using the third available secondary disk on your system. Mount it permanently using a UUID.
 
21.  Activate a network-latency tuned profile on your system.
 
22.  You forgot the root password on the virtual machine. Reboot the VM and reset your root password.
23. Using tempfiles, create a temporary directory named mylogs in ` /var/log ` with world permissions.
24. Set your timezone to ` America/New_York `. Make sure NTP is active and synchronized.
#practice 