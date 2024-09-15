### man
The most helpful parts of a man page are at the bottom. You will find actual examples, and the **See Also** section. 

Use `man -k` to search the mandb. To update the mandb, just type ``mandb

Man pages are categorized in different sections.
- 1: Executable programs or shell commands
- 5: File formats and conventions
- 8: System Admin Commands

### Locate
If you're going to use this, make sure you have a cron job set up to update the database manually
### Find

Search for a file named `document.pdf` in the `/home/linuxize` directory
	- find /home/linuxize -type f -name document.pdf

The `exec` option lets us run commands on whatever file we just found.
Search for a file named `document.pdf` in the `/home/linuxize` directory, and then change its permissions. 
	- find /home/linuxize -type f -name document.pdf -exec chmod 0755 {} \;

The `{}` is the results placeholder, and the ``;`` is the delimiter. The `\` is just used to escape it