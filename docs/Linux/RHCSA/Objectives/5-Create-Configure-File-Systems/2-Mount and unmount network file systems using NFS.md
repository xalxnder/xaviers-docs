# Setting up an NFS Server

>[!TIP] You do not have to do this for the exam.
1. Make sure nfs is installed
	1. `systemctl status nfs-server`
2. If it is not, install it.
	1. `dnf install nfs-utils`
3. Create the share directory.
	1. `mkdir /data`
4. vim /etc/exports
	1. ![[Pasted image 20220827152726.png]]
5. systemctl enable --now nfs-server
6. Configure the firewall rules
7. firewall-cmd  --add-service=nfs
	1.` firewall-cmd  --add-service=mountd`
	2. `firewall-cmd  --add-service=rpc-bind`
	3. `firewall-cmd  --add-service=rpc-bind--permanent`
	4. `firewall-cmd  --add-service=rpc-bind --permanent`
	5. `firewall-cmd  --add-service=mountd --permanent`
	6. `firewall-cmd  --add-service=nfs --permanent`


# Mounting NFS Shares
1. `showmount -e {nfs-host}`
2. Add it in fstab
	1. ![[Pasted image 20220827153428.png]]
3. Check your work with `mount -a`
4. Reboot to test. 