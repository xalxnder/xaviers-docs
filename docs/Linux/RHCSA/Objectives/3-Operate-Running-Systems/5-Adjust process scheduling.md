# Using nice and renice
```bash

[ps aux | grep dd](<[root@RHCSA-MAIN etc]# nice -n 5 dd if=/dev/zero of=/dev/null &
[1] 12219

[root@RHCSA-MAIN etc]# ps aux |grep dd
root       12219 87.1  0.0 220992  1036 pts/3    RN   17:33   0:06 dd if=/dev/zero of=/dev/null

[root@RHCSA-MAIN etc]# renice -n 10 -p 12221

[root@RHCSA-MAIN etc]# renice -n 10 -p 12219
12219 (process ID) old priority 5, new priority 10

[root@RHCSA-MAIN etc]# ps aux |grep dd

root       12219 77.8  0.0 220992  1036 pts/3    RN   17:33   0:31 dd if=/dev/zero of=/dev/null
```

Use a `-` to increase priority and `+` tp decrease priority. 
>[! Warning] Never set priority to -20.


## Adjust process scheduling

The default process scheduling algorithm on RHEL is SCHED_OTHER

We can find what scheduling algorithm a process is using with first finding the pid

**pidof -s [process]**

![](https://connor-maher.com/wp-content/uploads/2020/02/word-image-66.png)

From there we can use chrt to find the scheduling policy and priority

**chrt -p [pid of process]**

![](https://connor-maher.com/wp-content/uploads/2020/02/word-image-67.png)

To see all scheduling policies use **chrt -m**

![](https://connor-maher.com/wp-content/uploads/2020/02/word-image-68.png)

To set a process to use a different scheduling policy use **chrt [flag of policy] [priority of 0 or higher if applicable] -p [pid]**

![](https://connor-maher.com/wp-content/uploads/2020/02/word-image-69.png)