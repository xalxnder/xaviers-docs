Tasks: Task 01: On VM1, set the system hostname to server1.example.com and alias server1 using the hostnamectl command. Make sure that the new hostname is reflected in the command prompt. (Exercises 16-1 and 16-5).  

Task 02: On server1, configure a network connection on the primary network device with IP address 192.168.0.243/24, gateway 192.168.0.1, and nameserver 192.168.0.1 using the nmcli command (use different IP assignments based on your lab environment). (Exercise 16-4). 

Task 03: On VM2, set the system hostname to server2.example.com and alias server2 using a manual method (modify file by hand). Make sure that the new hostname is reflected in the command prompt. (Exercises 16-1 and 16-5).  

Task 04: On server2, configure a network connection on the primary network device with IP address 192.168.0.244/24, gateway 192.168.0.1, and nameserver 192.168.0.1 using a manual method (create/modify file by hand). Use different IP assignments based on your lab environment. (Exercise 16-3).  


Task 05: Run “ping -c2 server2” on server1. Run “ping -c2 server1” on server2. You should see 0% loss in both outputs. (Exercise 16-5).  

Task 06: On server1 and server2, attach the RHEL 8 ISO image to the VM and mount it persistently to /mnt/sr0. Define access to both repositories and con- firm. (Exercise 10-1).

Task 07: On server1, add HTTP port 8300/tcp to the SELinux policy database persistently. (Exercise 21-3). 




Task 10: Configure NFS service on server2 and share the home directory for user60 (create user60 on both systems) with server1. Configure AutoFS indirect map on server1 to automatically mount the home directory under 
/nfsdir when user60 logs on to server1. (Exercises 5-1, 17-1, 17-4, and 17-5).  


Task 13: On server1, create a group called group30 with GID 3000, and add user60 and user80 to this group. Create a directory called /sdata, enable setgid bit on it, and add write permission bit for group members. Set ownership and owning group to root and group30. Create a file called file1 under /sdata as user60 and modify the file as user80 successfully. (Exercises 4-5, 6-4, and 6-6).  

Task 14: On server1, create directory /var/dir1 with full permissions for every- one. Disallow non-owners to remove files. Test by creating file /var/dir1/stkfile1 as user60 and removing it as user80. (Exercise 4-6).  

Task 15: On server1, search for all manual pages for the description containing the keyword “password” and redirect the output to file /var/tmp/man.out. (Chapter 02, topic Searching by Keyword, and Chapter 07, topic: Input, Out- put, and Error Redirections).  Task 16: On server1, create file lnfile1 under /var/tmp and create one hard link /var/tmp/lnfile2 and one soft link /boot/file1. Edit lnfile1 using one link at a time and confirm. (Exercises 3-2 and 3-3).  Task 17: On server1, install module postgresql version 9.6 (select a different non-default version if 9.6 is not available). (Exercise 10-5). Task 18: On server1, add the http service to the “external” firewalld zone persis- tently. (Exercise 201).  Task 19: On server1, set SELinux type shadow_t on a new file testfile1 in /usr and ensure that the context is not affected by a SELinux relabeling. (Exercises 21-1 and 21-2).  Task 20: Configure password-less ssh access for user60 from server1 to rhc- sa4. (Exercise 19-2).  Task 21: Write a bash shell script that checks for the existence of files (not directories) under the /usr/bin directory that begin with the letters “ac” and display their statistics (the stat command). (Chapter 22: Table 22-1 and Scrip- t07).  Task 22: On server1, launch a named container as user60 with host port 10000 mapped to container port 80. Employ the latest version of the ubi7 image. Configure a systemd service to auto-start the container without the need for user60 to log in. Validate port mapping using an appropriate podman subcom- mand. (Exercises 23-5 and 23-10).


Task 23: On server1, launch another named container as user60 with /host_- data01 mapped to /container_data01, one variable ENVIRON=Exam, and host port 1050 mapped to container port 1050. Use the latest version of the ubi8 image. Configure a separate systemd service to auto-start the container without the need for user60 to log in. Create a file under the shared directory and validate data persistence. Verify port mapping and variable settings using appropriate podman subcommands. (Exercises 23-5, 23-7, 23-8, and 23-10).