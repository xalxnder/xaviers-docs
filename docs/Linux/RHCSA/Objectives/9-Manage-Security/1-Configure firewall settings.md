# Firewalld
Firewalld uses different components to make firewalling easier:
- Service
- Zone
- Ports

# Adding a Service 
Lets say you want to add the ftp service.
1. `firewall-cmd --add-service=ftp`
2. Verify with `firewall-cmd --list-all`
3. This is not persistent, though. To make it so, you must add the permanent flag
	1. `firewall-cmd --add-service=ftp --permanent`
	2. `firewall-cmd --add-service=ftp`
