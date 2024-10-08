# Managing Servers

### Create Users/Groups and Configure Superuser Access on Both Servers


We're going to lay the groundwork here and use these local accounts for all the subsequent tasks. You can write a script to do this, or do it by hand, from the data in the input file for the script. The file contents are:

`manny:1010:dba_admin,dba_managers,dba_staff moe:1011:dba_admin,dba_staff jack:1012:dba_intern,dba_staff marcia:1013:it_staff,it_managers jan:1014:dba_admin,dba_staff cindy:1015:dba_intern,dba_staff`

Set all user passwords to `dbapass`. Also, change the users' PRIMARY groups' GID to match their UID. Don't forget to check their home directories to make sure permisisons are correct!

**Configure superuser access:**

Enable the following command aliases:

-   SOFTWARE
-   SERVICES
-   PROCESSES

Add a new command alias named "MESSAGES":

`/bin/tail -f /var/log/messages`

Enable superuser privilages for the following local groups:

-   dba_managers: everything
-   dba_admin: Command aliases: SOFTWARE, SERVICES, PROCESSES
-   dba_intern: Command alias: MESSAGES

### Configure `yum` Repositories on Both Servers and Install Packages/Modules

You'll need to configure three repositories and install some software:

**RHEL 8 BaseOS:**

-   Repository ID: [rhel-8-baseos-rhui-rpms]
-   The mirrorlist is: `https://rhui3.REGION.aws.ce.redhat.com/pulp/mirror/content/dist/rhel8/rhui/$releasever/$basearch/baseos/os`
-   The GPG key is located at: `/etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release`
-   You will need to add SSL configuration:

`sslverify=1 sslclientkey=/etc/pki/rhui/content-rhel8.key sslclientcert=/etc/pki/rhui/product/content-rhel8.crt sslcacert=/etc/pki/rhui/cdn.redhat.com-chain.crt`

**RHEL 8 AppStream:**

-   Repository ID: [rhel-8-appstream-rhui-rpms]
-   The mirrorlist is: `https://rhui3.REGION.aws.ce.redhat.com/pulp/mirror/content/dist/rhel8/rhui/$releasever/$basearch/appstream/os`
-   The GPG key is located at: `/etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release`
-   You will need to add SSL configuration:

`sslverify=1 sslclientkey=/etc/pki/rhui/content-rhel8.key sslclientcert=/etc/pki/rhui/product/content-rhel8.crt sslcacert=/etc/pki/rhui/cdn.redhat.com-chain.crt`

**EPEL:**

-   Repository ID: [epel]
-   The baseurl is: `https://download.fedoraproject.org/pub/epel/$releasever/Everything/$basearch`

Configure the repositories on the first server, then make an archive of the files, securely copy them to the second server, then unarchive the repository files on the second server.

**Install software on both servers:**

-   Install the default AppStream stream/profile for `container-tools`
-   Install the `youtube-dl` package (from EPEL)
-   Check for system updates, but don't install them

### Configure IP Addresses on the Second Network Interface on the First Server

On the first server, configure the second interface's IPv4/IPv6 addresses using `nmtui`.

**IP Addresses:**

-   IPv4: 10.0.1.20/24
-   IPv6: 2002:0a00:0114::/64
-   Manual, not Automatic (DHCP) for both interfaces
-   Only IP addresses, no other fields
-   Configure only, do not activate

### Configure Persistent Journals on Both Servers

By default, the `systemd` journal logs to memory in RHEL 8, in the location `/run/log/journal`. While this works fine, we'd like to make our journals _**persistent**_ across reboots.

Configure the `systemd` journal logs to be persistent on both servers, logging to `/var/log/journal`.

### Managing Tuned Profiles and Individual Processes

**On the first server:**

-   Set a merged `tuned` profile using the the `powersave` and `virtual-guest` profiles.
-   Start one `stress` process and adjust the `niceness` value to 19.
-   Adjust the `niceness` value of the `stress` process to 10.
-   Kill the `stress` process.

### Manage Scheduled Tasks on the First Server

Create one `at` task and one `cron` job on the first server:

-   The `at` job will create a file containing the string "The at job ran" in the file named `/web/html/at.html`, two minutes from the time you schedule it.
-   The `cron` job will append to the `/web/html/cron.html` file every minute, echoing the `date` to the file.

These files will be available via the web server on the first server after the "Troubleshoot SELinux issues" objective is completed.

### Configure Time Service Clients for Both Servers

Time sync is not working on either of our servers. We need to fix that.

Configure `chrony` to use the following server:

`server 169.254.169.123 iburst`

Make sure your work is persistent and check your work!

### Managing the System Bootloader

On server1, make the following changes:

-   Increase the timeout using `GRUB_TIMEOUT=10`
-   Add the following line: `GRUB_TIMEOUT_STYLE=hidden`
-   Add `quiet` to the end of the `GRUB_CMDLINE_LINUX` line

Validate the changes in `/boot/grub2/grub.cfg`. Do not reboot the server.




# Managing Storage
### Add Swap Space Persistently and Nondisruptive

We need to increase the swap on the second server. We're going to use half of our first unused 2G disk for this additional swap space. Configure the swap space _**non-destructively**_ and _**persistently**_.



### Configure `autofs` for Home Directories

Configure `autofs` on the NFS_SERVER to mount the user home directories on the main server at `/export/home`.

-   On the NFS_SERVER, configure a NFS server with the following export:

`/home <first_server_private_IP>(rw,sync,no_root_squash)`

-   On the first server, configure `autofs` to mount the exported `/home` directory on the second server at `/export/home`. Change the home directories for our six users (manny|moe|jack|marcia|jan|cindy) to be `/export/home/<user>` and test.



# Managing Containers

### Create a Persistent `systemd` Container Using Podman

**As the `cloud_user` user on the first server, create a _persistent `systemd` container_ with the following:**

-   Image: registry.access.redhat.com/rhscl/httpd-24-rhel7
-   Port mappings: 8080 on the container to 8000 on the host
-   Persistent storage at `~/web_data`, mounted at `/var/www/html` in the container
-   Container name: web_server 

Test the container to make sure when you run a curl, it displays the contents of `~/web_data/test.txt`


