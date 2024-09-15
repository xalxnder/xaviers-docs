# Setting up a Base Server
- Install two servers using the minimal installation pattern. 
- Use the names server1.example.com and server2.example.com and use DHCP to get an IP address from the local DNS server.
- Ensure that the partition for / is 15 GiB. Also create a 1 GiB swap partition. **Do NOT register the servers with Red Hat.**



# Resetting the Root Password
- Use the appropriate solution to reset the root password on server2, assuming that you have lost the root password and you have no administrator access to the server anymore



# Configuring a Repository
- On both servers, create an ISO file based on the installationDVD. Mount this ISO file persistently and configure the servers to use the local ISO file as the repositories. After successfully completing this assignment, you should be able to install software on both servers.


# Managing Partitions
- On server1, use your virtualization software to increase the size of your primary disk in such a way that at least 10 GiB of unallocated disk space is available
- In the free disk space, create a 1 GiB partition and format it with the vfat filesystem. 
- Make sure it is mounted persistently on the /winfile directory.
- Also create a 1 GiB swap partition and ensure it is mounted persistently



# Managing LVM Logical Volumes
- Create a logical volume with the name myfiles. 
	- Ensure it uses 8 MiB extents. 
	- Configure the volume to use 75 extents. 
	- Format it with the ext4 file system and ensure it mounts persistently on /myfiles
- Increase the size of the / logical volume by 5 GiB
- If volume groups need to be created, create them as needed

# Creating Users and Groups
- Create a user lisa. Ensure she has the password set to "password" and is using UID 1234. She must be a member of the secondary group sales
- Create a user myapp. Ensure this user cannot open an interactive shell

### Configure a Shared Directory for Collaboration

**On the second server:**

Create a directory at `/home/dba_docs` with:

-   Group ownership: dba_staff
-   Permissions: 770
-   Set-GID set
-   Sticky bit set

Create a link in each shared user's home directory to this directory, for easy access.

Set the following ACLs:

-   Read-only for `jack` and `cindy`
-   Full permissions for `marcia` 


# Managing Permissions
- Create a shared group directory /sales and ensure that lisa is the owner of that directory. 
- The owner and the group sales should have permissions to access this directory and read and write files in it. Other users should have no permissions at all.
- Ensure that any new file that is created in this directory is group-owned by the group sales automatically.

# Scheduling Jobs
Schedule a job that writes "hello folks" to syslog every Monday through Friday at 2 AM. Make sure this job is executed as the user lisa.

Create one `at` task and one `cron` job on the first server:

-   The `at` job will create a file containing the string "The at job ran" in the file named `/web/html/at.html`, two minutes from the time you schedule it.
`{command} | at now +2 minutes`
-   The `cron` job will append to the `/web/html/cron.html` file every minute, echoing the `date` to the file.


# Managing Containers as Services
- Create a container with the name mydb that runs the mariadb database as user lisa. 
- The container should automatically be started at system start, regardless of whether or not user lisa is logging in. 
- The container further should meet the following requirements: 
	- The host directory /home/lisa/mydb is mounted on the container, directory /var/lib/mysql
	- The container is accessible on host port 3206
	- You do not have to create any databases in it.

# Managing Automount
- On server2, create the directories /homes/user1 and /homes/user2.
- Use NFS to share these directories and ensure the firewall does not block access to these directories. 
- On server1, create a solution that automatically, on-demand mounts `server2:/homes/user1` on `/homes/user1`, and also that automatically, on-demand mounts `server2:/homes/user2` on `/homes/user2` when these directories are accessed


# Setting Time
- Configure server1 and server2 as an NTP client for pool.ntp.org


# Managing SELinux
- Ensure that the Apache web server is installed and configure it to offer access on port 82
- Copy the file `/etc/hosts` to `/tmp/hosts`. Next, move `/tmp/hosts` to the directory `/var/www/html/hosts` and ensure this file can be accessed by the Apache web server

## Managing Processes
- Create a user a linda and open a shell as this user 
- As linda, run two background processes sleep 600; one of them with the highest possible priority, the other one with the lowest possible priority 
- Use the most efficient way to terminate all current sessions for user linda


### Logging
Configure persistent logging to `/var/log/journal` on server 1


### Managing the System Bootloader

On server1, make the following changes:

-   Increase the timeout using `GRUB_TIMEOUT=10`
-   Add the following line: `GRUB_TIMEOUT_STYLE=hidden`
-   Add `quiet` to the end of the `GRUB_CMDLINE_LINUX` line

Validate the changes in `/boot/grub2/grub.cfg`. Do not reboot the server.


#practice-exam  #practice