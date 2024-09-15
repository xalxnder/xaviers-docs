 

1. Using a manual method (create/modify files by hand), configure a network connection on the primary network device with IP address 192.168.0.241/24, gateway 192.168.0.1, and nameserver 192.168.0.1. Use different IP assignments based on your lab setup. (Exercise 16-3). 
2. Using a manual method (modify file by hand), set the system host- name to rhcsa1.example.com and alias rhcsa1. Make sure that the new host- name is reflected in the command prompt. (Exercises 16-1 and 16-5).  
3. Set the default boot target to multi-user. (Chapter 12, topic: Managing Target Units).  
4. Set SELinux to permissive mode. 

5. Perform a case-insensitive search for all lines in the /usr/share/dict/ linux.-words file that begin with the pattern “essential”. Redirect the output to `/var/tmp/pattern.txt `file. Make sure that empty lines are omitted. (Chapter 07, topic: Regular Expressions).

6.  Create user accounts called lisa, tom, and bob. Set their passwords to Temp1234. Make lisa and bob accounts to expire on December 31, 2021. 

7. Create a group called devs and add tom and bob as secondary members. (Exercise 6

8. Create a user account called ashley with UID 2929. Set the password to user1234. (Exercise 5-2).  

9. Create a directory called dir1 under /var/tmp with ownership and owning group set to root. Configure default ACLs on the directory and give lisa read, write, and execute permissions. (Exercise 4-8).  

10. Create a logical volume called lvol1 of size 280MB in vgtest volume group. Mount the ext4 file system persistently to /mnt/mnt1. 

11. Change group membership on /mnt/mnt1 to devs. Set read/write/ execute permissions on /mnt/mnt1 for group members, and revoke all permissions for public. 

12. Create a logical volume called lvswap of size 280MB in vgtest volume group. Initialize the logical volume for swap use. Use the UUID and place an entry for persistence.

13. Use the combination of tar and bzip2 commands to create a compressed archive of the /usr/lib directory. Store the archive under /var/tmp as usr.tar.bz2. 

14. Create a directory hierarchy /dir1/dir2/dir3/dir4 and apply SELinux contexts of /etc on it recursively. (Chapter 03, topic:


15. Task 18: Enable access to the atd service for tom and deny for bob. (Chapter 08, topic: Controlling User Access).  
	/etc/at.deny
	/etc/cron.deny

16. Allow tom to use sudo without being prompted for their password. (Chapter 06, topic: Doing as Superuser (or Doing as Substitute User)).  

17. Write a bash shell script to create three user accounts—user555, user666, and user777—with no login shell and passwords matching their user- names. The script should also extract the three usernames from the /etc/ passwd file and redirect them into /var/tmp/newusers. (Chapter 22: Script12 and Chapter 07, topics: Regular Expressions, and Input, Output, and Error Redirections).  

18. Launch a simple container as tom using the latest version of ubi7 image. Configure the container to auto-start at system reboots without the need for tom to log in. (Exercise 23-10).  

19. Launch another container as tom using the latest version of ubi8 image with two environment variables SHELL and HOSTNAME. Configure the container to auto-start via systemd without the need for tom to log in.