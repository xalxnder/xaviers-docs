
The `no__root__squash` option in `/etc/exports` is extremely unsafe to use. By default, NFS shares change the root user to the `nfsnobody` user, an unprivileged user account. This prevents a client computer’s root user from being able to change all files and directories in the shared filesystem. For RHCSA this option is ok, but elsewhere, don't use it.

#nfs #squash