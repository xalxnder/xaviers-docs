
Display all lines containing the string bash in /etc/passwd
	- grep bash /etc/passwd

Display the lines that do NOT contain the string 'nologin'
	- grep -v nologin /etc/passwd

Search for the string 'linuxize.com' in all files inside the /etc/directory
	- grep -r 'linuxize.com' /etc

Searh for the string linux at the beginning of the line in file.txt
	- grep '^linux' file.txt


