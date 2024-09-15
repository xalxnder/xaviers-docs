
To get info about what is happening on your machine use the following 3 approaches:
1.  Monitor the files in `/var/log` that are written by `rsyslogd`.
2.  Use the `journalctl` command to get more detailed information from the journal.
3.  Use the `systemctl status <unit>` command to get a short overview of the last significant events that have been logged by Systemd units through `journald`.