---
title: 5.7 Pod Troubleshooting
---


# Troubleshooting Commands

- `kubectl get pods` Checks the current pod status
- `kubectl describe pod {podname}` gets more info about pod status 
- `kubectl logs {podname}` Grabs the logs
- `kubectl exec -it podname sh` Opens a shell on the Pod to analyze specific components


# Scenario

`kubectl run mydb --image=mariadb`

```bash
[xavier@xa-dev-main ~]$ kubectl get pods
NAME                        READY   STATUS             RESTARTS      AGE
firstapp-57d8d5d97f-gcrhl   1/1     Running            0             6d8h
mydb                        0/1     CrashLoopBackOff   1 (14s ago)   27s
myginx                      1/1     Running            0             18h
```
We can see mydb failed :(. Lets investigate

```bash
[xavier@xa-dev-main ~]$ kubectl logs mydb
2024-09-29 08:59:57+00:00 [Note] [Entrypoint]: Entrypoint script for MariaDB Server 1:11.5.2+maria~ubu2404 started.
2024-09-29 08:59:57+00:00 [Warn] [Entrypoint]: /sys/fs/cgroup///memory.pressure not writable, functionality unavailable to MariaDB
2024-09-29 08:59:57+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'
2024-09-29 08:59:57+00:00 [Note] [Entrypoint]: Entrypoint script for MariaDB Server 1:11.5.2+maria~ubu2404 started.
2024-09-29 08:59:57+00:00 [ERROR] [Entrypoint]: Database is uninitialized and password option is not specified
	You need to specify one of MARIADB_ROOT_PASSWORD, MARIADB_ROOT_PASSWORD_HASH, MARIADB_ALLOW_EMPTY_ROOT_PASSWORD and MARIADB_RANDOM_ROOT_PASSWORD
```

As we can see, we forgot to specify environment variables when creating the pod.