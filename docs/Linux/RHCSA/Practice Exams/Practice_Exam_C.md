
2.  Create user `student` with password password, and user root with password password.
5.  Set default values for new users. Make sure that any new user password has a length of at least six characters and must be used for at least three days before it can be reset
	6. /etc/login.defs
6.  Create users `edwin` and `santos` and make them members of the group sales as a secondary group membership. Also, create users serene and alex and make them members of the group account as a secondary group.
7.  Create shared group directories /groups/sales and /groups/account, and make sure these groups meet the following requirements:
	1. Members of the group sales have full access to their directory.
	2. Members of the group account have full access to their directory.
	3. Users have permissions to delete only their own files, but alex is the general manager, so user alex has access to delete all users’ files.
8. Create a 4-GiB volume group, using a physical extent size of 2 MiB. In this volume group, create a 1-GiB logical volume with the name myfiles and mount it persistently on /myfiles.
9. Create a group sysadmins. Make users edwin and santos members of this group and ensure that all members of this group can run all administrative commands using sudo.
10. Optimize your server with the appropriate profile that optimizes throughput.   
11. Configure your server to synchronize time with serverabc.example.com, where serverabc is an alias to myserver.example.com. Note that this server does not have to exist to accomplish this exercise.
12. Configure a web server to use the nondefault document root /webfiles. In this directory, create a file index.html that has the contents hello world and then test that it works.
13. Configure your system to automatically start a mariadb container. This container should expose its services at port 3306 and use the directory /var/ mariadb-container on the host for persistent storage of files it writes to the /var directory.
14. Configure your system such that the container created in step 13 is automatically started as a Systemd user container.

#practice-exam 