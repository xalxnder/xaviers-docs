To add persistent storage to Podman containers, you bind-mount a directory on the host operating system into the container. A bind-mount is a specific type of mount, where a directory is mounted instead of a block device.
To set up this storage solution, you need to prep first:

For this example, we're using the `mariadb` image
1. `podman run -d --name mydb -e MYSQL_ROOT_PASSWORD=password mariadb
2. Make the directory you want to mount. Make sure this is in the user's home directory. 
3. `podman unshare chown 27:27 mydb
	1. podman-unshare - Run a command inside of a modified user namespace
	2. The 27 is the mariadb's UID inside of the container
4. `podman stop mydb
5. `podman rm mydb

Ok, now for the SELinux
1. The file context of the mydb directory is currently `user_home_t`. This needs to be changed, because SELinux won't allow us to bind directory to a directory that has this context. 
2. `podman run -d --name mydb -e MYSQL_ROOT_PASSWORD=password -v /home/xavier/mydb:/var/lib/mysql:Z mariadb
	1. The `:Z` takes care of the SELinux
3. Finally, verify  with ls on mydb, and you will see the directories from the container. 
	1. ![[Pasted image 20220913070924.png]]