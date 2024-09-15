	`1`#### Configuring `autofs` to mount home directories on `server1`

1.  Become `root`:
    
    `sudo -i`
    
2.  Install the `autofs` package:
    
    `yum -y install autofs`
    
3.  Create the `/export/home` directory:
    
    `mkdir -p /export/home`
    
4.  Add the mapping for the `/export/home` directory to `/etc/auto.master`:
    
    `vi /etc/auto.master`
    
5.  At the end of the file, above the line with `+auto.master`, add:
    
    `/export/home /etc/auto.home`
    
6.  Save and quit:
    
    `:wq`
    
7.  Edit `/etc/auto.home`:
    
    `vi /etc/auto.home`
    
8.  Add the following line: **(NOTE: Use command `ip addr` on `server2` for private IP address)**
    
    `* <second_server_private_IP>:/home/&`
    
9.  Save and quit:
    
    `:wq`
    
10.  Confirm NFS export:
    
    `showmount -e <second_server_private_IP>`
    
11.  Start and enable `autofs` service:
    
    `systemctl enable --now autofs`
    
12.  Check `autofs` status:
    
    `systemctl status autofs`
    
13.  On `server1`, change user's home directory locations to `/export/home`:
    
    `for i in manny moe jack marcia jan cindy; do usermod -d /export/home/$i $i; done`
    
14.  Confirm changes:
    
    `grep -E 'manny|moe|jack|marcia|jan|cindy' /etc/passwd`
    
15.  On `server1`, test as the user `manny`:
    
    `su - manny`
    
16.  Check directory:
    
    `pwd`
    
17.  Create a file:
    
    `touch file1`
    
18.  Create a directory:
    
    `mkdir directory1`
    
19.  Check our work:
    
    `ls -la`
    
20.  Log out `manny`:
    
    `exit`
    
21.  On `server1`, test as `moe`:
    
    `su - moe`
    
22.  Check directory:
    
    `pwd`
    
23.  Create a file:
    
    `touch file1`
    
24.  Create a directory:
    
    `mkdir directory1`
    
25.  Check our work:
    
    `ls -la`
    
26.  Log out `moe`:
    
    `exit`
    
27.  On `server1`, test as `jack`:
    
    `su - jack`
    
28.  Check directory:
    
    `pwd`
    
29.  Create a file:
    
    `touch file1`
    
30.  Create a directory:
    
    `mkdir directory1`
    
31.  Check our work:
    
    `ls -la`
    
32.  Log out `jack`:
    
    `exit`
    
33.  Confirm that the home directories are mounted via `autofs` on the first server:
    
    `mount | grep home`