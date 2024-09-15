# Command Line Tools For Process Management
| Command | Explanation                           |
| ------- | ------------------------------------- |
| ps      | Show an overview of current processes |
| ps -ef        |                                       |
ps
ps -ef
ps fax
ps aux |grep dd 
pgrep dd

# Kill Killall and pkill
| Signal      | Explanation                     |
| ----------- | ------------------------------- |
| SIGTERM(15) | Used to ASK a process to stop   |
| SIGTERM(9)  | Used to FORCE a process to stop |
| SIGHUP (1)  | Used to HANG UP a process. The process will reread its config files. Like a restart.                                |

To send one of these signals, use `kill`.