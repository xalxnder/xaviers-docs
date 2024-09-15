For any non-default port access, use `semanage port` to apply the correct label to the port.

>[!TIP] Please use `man semanage-port` for help on the exam. It literally has examples. 


#### Scenario 
- We changed the default sshd port to `2022`
- When attempting to restart the service, it failed. 
- When checking `grep AVC /var/log/audit/audit.log`, we saw the following:
	- ![[Pasted image 20220911084509.png]]
	- Ok, let's check the man page.
		- ![[Pasted image 20220911084548.png]]
- Cool, we see our example. So run that command.
	- [root@RHCSA-MAIN html]# semanage port -a -t ssh_port_t -p tcp 2022
	- If you get an error that context is already assigned, you need to use `-m`, instead of `-a`