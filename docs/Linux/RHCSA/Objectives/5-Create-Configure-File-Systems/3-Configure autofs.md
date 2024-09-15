# Understanding Automount

Automount is implemented by the autofs service that takes care of mounting a share when an attempt is made to access it. That means it is mounted on demand and that it does not have to be mounted permanently. An important benefit of using automount is that it works completely in user space and, contrary to mounts that are made through the mount command, no root permissions are required.

1.  Make sure autofs is installed.
	1. `yum install -y autofs` 
2.  Type showmount -e {NFS HOST}, which shows you NFS exports offered by server2.
	1. ![[Pasted image 20220907183044.png]]
3.  Open the file `/etc/auto.master` and add the mount point, and the secondary file:
	4. ![[Screen Shot 2022-09-07 at 6.50.47 PM.png]]
4. Next create the secondary file. In this example, it will be /etc/auto.files. In this file, you'll add the mount point directory as a relative filename, NFS options, and the server and share name. 
	1. ![[Pasted image 20220907185411.png]]
5. `systemctl restart autofs`
6. `systemctl enable --now autofs`
7. Verify with mount and grep commands
	1. ![[Pasted image 20220907190311.png]]

# Automount on home directories

To setup these examples, just create new users with home directories that don't already exist. 
1. On your NFS server, add your new export
	1. ![[Pasted image 20220908065744.png]]
	2. restart nfs
	3. Back on your main server edit the `/etc/auto.master` file
		1. ![[Pasted image 20220908065927.png]]
	4. Edit the corresponding map file. In this case, its `/etc/auto.ldap`
		1. ![[Pasted image 20220908070016.png]]
	5. `systemctl restart autofs`

