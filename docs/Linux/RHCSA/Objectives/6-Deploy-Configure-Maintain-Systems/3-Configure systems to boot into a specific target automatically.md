To view the current default target (what target is being used for the current boot process:

`systemctl get-default`

To list all of the currently loaded targets units (as called by the master target):

`systemctl list-units --type target`
- The command will only show the currently active units, to show all units:

`systemctl list-units --type target --all`

To change the default target:

`systemctl set-default multi-user.target`