
# Setting Default Permissions with umask
If you do not use ACLs, there is a shell setting that determines the default permissions that you will get: `umask`. Default permissions for a file are **666**. Default permissions for a directory are **777**. 
```bash
666 - 022 = 644
-rw-r--r--. 1 root   root      0 Jul  9 06:22 test1
6    4    4
```

So if we wanted to give every new file, read, read, and no permissions we'd run `umask  226`

```bash
666 - 226 = 440
-r--r-----. 1 root   root      0 Jul  9 06:26 test2
4   4   0
```

To make the default file permissions 777(NOT RECOMMENDED), run `umask 000`
