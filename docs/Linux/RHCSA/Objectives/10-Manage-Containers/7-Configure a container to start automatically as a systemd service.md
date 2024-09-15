### Containers As Services 
On a standalone platform where containers are running rootless containers, systemd is needed to autostart containers. To automatically start containers in standalone situation, you can create systemd user unit files for rootless containers and manage them with `systemctl` .

In systemd, services are easily started and enabled with root permissions using commands like systemctl enable --now myservice.service. If no root permissions are available, you need to use systemctl --user. The --user option allows users to run the common systemd commands, but in user space only. This works for any service that can run without root permissions.

When systemctl --user is used, services can be automatically started  only when a user session is started. To define an exception to that, you can use the loginctl session manager, which is part of the systemd solution to enable “linger” for a specific user account. If you use `loginctl enable-linger myuser`, you enable this for the user myuser. When **linger** is enabled, systemd services that are enabled for that specific user will be started on system start, not only when the user is logging in.

#### The Process
1.  Use sudo useradd linda to create a user linda.
2.  Use `sudo passwd linda` to set the password for user linda.
3.  Type `sudo loginctl enable-linger linda` to enable the linger feature for user linda.
4.  Log in as user linda (DON'T USE `su -`).
	1. `ssh linda@localhost
5.  Type `mkdir -p ~/.config/systemd/user; cd ~/.config/systemd/user` to create and activate the directory where the systemd user files will be created. Yes the directory must  be named user. 
6.  Use `podman run -d --name mynginx -p 8081:80 nginx` to start an nginx pod.
7.  Type `podman ps` to verify the nginx pod has been started.
8.  Create the systemd user files using `podman generate systemd --name mynginx --files --new`.
	1.  A systemd unit file with the name `container-mynginx.service` is created.
9.  Use `vim container-mynginx.service` and change the WantedBy line such that it reads `WantedBy=default.target`.
10.  Type `systemctl --user daemon-reload` to ensure that systemd picks up the changes.
11.  Use `systemctl --user enable container-mynginx.service` to enable the systemd user service. (Do not try to start it because it has already been started!)
12.  Type `systemctl --user status container-mynginx.service` to verify the service has the state of enabled.
13.  Reboot your server, login NOT AS linda and after rebooting, verify that the container is automatically started.