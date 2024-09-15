#  Why does catting a file to itself erase it?
```sh
➜  Bash cat input.txt
manny:1010:dba_admin,dba_managers,dba_staff moe:1011:dba_admin,dba_staff jack:1012:dba_intern,dba_staff marcia:1013:it_staff,it_managers jan:1014:dba_admin,dba_staff cindy:1015:dba_intern,dba_staff

➜  Bash sed 's/ /\n/g' input.txt
manny:1010:dba_admin,dba_managers,dba_staff
moe:1011:dba_admin,dba_staff
jack:1012:dba_intern,dba_staff
marcia:1013:it_staff,it_managers
jan:1014:dba_admin,dba_staff
cindy:1015:dba_intern,dba_staff

➜  Bash sed 's/ /\n/g' input.txt > input.txt
➜  Bash cat input.txt
```


Consider [3.1.1 Shell Operation](https://www.gnu.org/software/bash/manual/bash.html#Shell-Operation), particularly the order in which things are done:

-   redirections are processed **before** the command is actually executed, but
-   expansions are processed before redirections.

So in the above example, the shell truncates `input.txt`, THEN attempts to run the sed command. Since, input.txt has already been truncated, `sed` is working with an empty file.

TLDR;

DON'T DO THIS :) 