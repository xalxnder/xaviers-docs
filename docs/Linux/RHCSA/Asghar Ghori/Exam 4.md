Task 01: On VM1, set the system hostname to rhcsa5.example.com and alias rhcsa5 using the hostnamectl command. Make sure that the new hostname is reflected in the command prompt. (Exercises 16-1 and 16-5).

Task 02: On rhcsa5, configure a network connection on the primary network device with IP address 192.168.0.245/24, gateway 192.168.0.1, and nameserver 192.168.0.1 using the nmcli command. Use different IP assignments based on your lab environment. (Exercise 16-4). 

Task 03: On VM2, set the system hostname to rhcsa6.example.com and alias rhcsa6 using a manual method (modify file by hand). Make sure that the new hostname is reflected in the command prompt. (Exercises 16-1 and 16-5).  

Task 04: On rhcsa6, configure a network connection on the primary network device with IP address 192.168.0.246/24, gateway 192.168.0.1, and nameserver 192.168.0.1 using a manual method (create/modify files by hand). Use different IP assignments based on your lab environment. (Exercise 16-3).  Task 05: Run “ping -c2 rhcsa6” on rhcsa5. Run “ping -c2 rhcsa5” on rhcsa6. You should see 0% loss in both outputs. (Exercise 16-5).  


Task 07: Export /share5 on rhcsa5 and mount it to /share6 persistently on rhcsa6. (Exercises 17-1 and 17-

2).  Task 08: Use NFS to export home directories for all users (u1, u2, and u3) on rhcsa6 so that their home directories become available under /home1 when they log on to rhcsa5. Create u1, u2, and u3. (Exercises 17-1 and 17-

Task 09: On rhcsa5, add HTTP port 8400/udp to tman he public zone persistently.

Task 10: Configure password less ssh access for u1 from rhcsa5 to rhcsa6. Copy the directory /etc/sysconfig from rhcsa5 to rhcsa6 under /var/tmp/ remote securely.


Task 12: On rhcsa6, install module “container-tools” stream rhel8. (Exercise 10-5).  


Task 14: On rhcsa5 and rhcsa6, set the tuning profile to powersave. (Exercise 12-2).  

Task 15: On rhcsa5, create file lnfile1 under /var/tmp and create three hard links called hard1, hard2, and hard3 for it. Identify the inode number associated with all four files. Edit any of the files and observe the metadata for all the files for confirmation. (Exercise 3-2).  

Task 16: On rhcsa5, members (user100 and user200) of group100 should be able to collaborate on files under /shared but cannot delete each other’s files. (Exercises 4-5 and 4-

Task 17: Synchronize the entire /etc directory on rhcsa5 to /var/tmp/etc on rhc- sa6. Use in-transit compression. Capture the output and any errors in the /var/ tmp/etc.transfer file on rhcsa5 during the synchronization process. (Chapter 19, topic: Synchronizing Files Remotely Using rsync, and Chapter 07, topic: Regular Expressions).  

Task 18: On rhcsa6, list all files that are part of the “setup” package, and use regular expressions and I/O redirection to send the output lines containing “hosts” to /var/tmp/setup.pkg. (Exercise 9-2, and Chapter 07, topics: Regular Expressions, and Input, Output, and Error Redirections).  

Task 20: On rhcsa5, configure journald to store messages permanently under /var/log/journal and fall back to memory-only option if /var/log/journal direc- tory does not exist or has permission/access issues. (Exercise 12-1).  

Task 21: Write a bash shell script that defines an environment variable called ENV1=book1 and creates a user account that matches the value of the variable. (Chapter 22: Script02 and Script03).  

Task 22: On rhcsa5, launch a named root container with host port 443 mapped to container port 443. Employ the latest version of the ubi7 image. Configure a systemd service to auto-start the container at system reboots. Validate port mapping using an appropriate podman subcommand. (Exercises 23-5 and 

Task 23: On rhcsa5, launch a named container as user100 with /data01 mapped to /data01 and two variables KERN=$(uname -r) and SHELL defined. 
- Use the latest version of the ubi8 image.
- Configure a systemd service to auto- start the container at system reboots without the need for user100 to log in. 
- Create a file under the shared mount point and validate data persistence. Verify port mapping using an appropriate podman subcommand. (Exercises 23-7, 23-8, and 23-10).