There is no internet connection on the machines, so you have to install locally.
# Local
`dnf config-manager --add-repo="file:///repo/BaseOS"`
`dnf config-manager --add-repo="file:///repo/AppStrem"`
Verify with `ls /etc/yum.repos.d`

If dnf confg-manager isnt installed, you'll want to know how to do this by creating repo files.

### Not On The Exam
1. MAKE SURE YOUR DISC IS ACTUALLY LOADED
2. `dd if=/dev/sr0 of=/{NAME_OF_ISO} bs=1M`
	1. if is the input file, and of is the output file.
3. `mkdir /repo`
4. vim /etc/fstab
	1. Add the following line:
		1. /rhel9.iso              /repo                   iso9660 defaults        0 0
5. `systemctl daemon-reload`
6. `mount -a`




Create two files
	1. `/etc/yum.repos.d/appstream.repo`
	2. `/etc/yum.repos.d/base.repo`

```bash
[appstream]
name=appstream
baseurl=file:///repo/AppStream
gpgcheck=0       
```


```bash
[base]
name=base
baseurl=file:///repo/BaseOS
gpgcheck=0
```
To tell your server which repository to use, you need to create a file with a name that ends in .repo in the directory /etc/yum.repos.d. In that file you need the following contents