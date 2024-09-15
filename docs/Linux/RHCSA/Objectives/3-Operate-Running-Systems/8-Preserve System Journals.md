# Preserving the Systemd Journal
By default, the journal is stored in the file `/run/log/journal`. The entire /run directory is used for current process status information only, which means that the journal is cleared when the system reboots. To make the journal persistent between system restarts, you should make sure that a directory `/var/log/journal` exists. Yes, all you need to do is create this directory. The system will handle the rest. 

Storing the journal permanently requires setting the Storage=auto parameter in` /etc/systemd/journal.conf`. This parameter can have different values:

-   `Storage=auto` The journal will be written on disk if the directory /var/log/journal exists.
-   `Storage=volatile` The journal will be stored only in the /run/log/ journal directory.    
-   `Storage=persistent `The journal will be stored on disk in the directory /var/log/journal. This directory will be created automatically if it doesn’t exist.
-   `Storage=none` No data will be stored, but forwarding to other targets such as the kernel log buffer or syslog will still work.

>[!WARNING]  The journal is NOT kept forever. The journal has built-in log rotation that will be used monthly. To change these settings, you can modify the file `/etc/systemd/journald.conf`.

# Instructions
### Create a storage directory
First, create a journal directory under the `/var/log` directory:
```shell
[server]$ sudo mkdir /var/log/journal
```

### Edit the journald.conf file

Edit the file `/etc/systemd/journald.conf` and set the **Storage** parameter to **persistent** (it is set to **auto** by default):
```shell
[server]$ sudo vim /etc/systemd/journald.conf
[Journal]
Storage=persistent 
[...]
```

### Restart systemd-journald
Next, restart the **systemd-journald** service:

```shell
[server]$ systemctl restart systemd-journald
```

### Reboot the server
Finally, reboot the server to confirm the persistence of entries by listing the `/var/log/journal` content. You should have output that looks similar to this:

```shell
[server]$ ls /var/log/journal
75ab164a278e48be9cf80d80716a8cd9
```