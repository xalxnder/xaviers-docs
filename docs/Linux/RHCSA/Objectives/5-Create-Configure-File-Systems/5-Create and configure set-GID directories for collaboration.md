### Scenario
- shelly and linda are both apart of the profs group.
- They want to share files in the `/data/profs` directory. 
- Linda creates a file, and wants shelly to edit it. Without SGID, this is impossible because when linda creates a file, she becomes the owner, and group of that file. 
	- ![[Pasted image 20220909072650.png]]
- To get around this, set up SGID on that directory.
	- `chmod 2770 /data/profs/`
- Now, whenever a file is created in this directory, the group owner of the directory becomes the group owner of file. In this case, `profs`
	- ![[Pasted image 20220909072924.png]]
- chmod 660 to make sure the file can actually be edited by group members. 
	- ![[Pasted image 20220909073039.png]]
- Now shelly can edit `linda1` !!
	  