## Archiving and Compression

	ARCHIVING AND COMPRESSING ARE NOT THE SAME THING

### Archiving with Tar


### Create 
tar -cf `{archive}` `{what you are archiving}`
### Extract 
tar -xf  `{archive}` `{what you are archiving}`



| Option | Use                                                                   |
| ------ | --------------------------------------------------------------------- |
| c      | Creates an archive.                                                   |
| v      | Shows verbose output while tar is working.                            |
| t      | Shows the contents of an archive.                                     |
| z      | Compresses/decompresses the archive while creating it, by using gzip. |
| j      | Compresses/decompresses the archive by using bzip2.                   |
| x      | Extracts an archive.                                                  |
| u      | Updates an archive; only newer files will be written to the archive.  |
| C      | Changes the working directory before performing the command.          |
| r      | Appends files to an archive.                                                                      |

### Compression
#### gzip
gzip `filename`.    To uncompress, use gunzip
#### bzip2
bzip `filename`



# Lab
1.  Log is user root. In the home directory of root, create one archive file that contains the contents of the `/home` directory and the `/etc` directory. Use the name `/root/essentials.tar `for the archive
	1. `tar -cf essentials.tar /home /etc`
2.  Copy this archive to the /tmp directory. Also create a hard link to this file in the / directory.
	1. `cp essentials.tar /tmp`
	2. `ln /tmp/essentials.tar .`
3.  Rename the file `/essentials.tar` to `/archive.tar`.
	1. `mv essentials.tar archive.tar`
4.  Create a symbolic link in the home directory of the user root that refers to  /archive.tar. Use the name link.tar for the symbolic link.
	1. `ln -s /archive.tar`
6.  Compress the /root/essentials.tar file.
	1. `gzip essentials.tar`
7. Create a directory structure `/tmp/files/pictures`, `tmp/files/photos`, and `tmp/files/videos`
	1. `mkdir -p /tmp/files/{pictures,photos,videos}`
8. Copy all files that have a name starting with a,b,or c from /etc to /tmp/files
	1. `cd /etc`
	2. `cp -r [a-c]* /tmp/files/`
9. From /tmp/files, move all files that have a name starting with an a, or b to `tmp/files/photos`, and files starting with a c to `tmp/files/videos`
	1. `mv [a,b]* photos/`
	2. `mv c* videos/`
10. Find all files in `/etc` that have a size smaller than 1000 bytes and copy those to `tmp/files/pictures`
	1. `find /etc -type f -size -1000c -exec cp {} /tmp/files/pictures/  \;`
11. In `/tmp/files`, create a symbolic link to /var
	1. `ln -s /tmp/files`
12. Create a compressed archive file of the `/home directory`
	1. `tar -czvf home.tgz /home/`
13. Extract this compressed archive with relative file names in `/tmp/archive`
	1. `tar -xvf home.tar`