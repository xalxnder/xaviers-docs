- hostnamectl set-hostname to manage hostnames
- To resolve hostnames, /etc/hosts is used 
	- ![[Pasted image 20220910171858.png]]
		- The first part is the ip address
		- The 2nd part is the FDQN
		- The third part is the short name. 

If you're connecting to the world wide web, you'll want to use /etc/resolv.conf for DNS

Finally, the order of host name resolution is determined through `/etc/nsswitch.conf`