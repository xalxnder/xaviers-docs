### Understanding Read, Write, and Execute
| **Permission** | **Applied To Files**          | **Applied to Directories**     |
| ---------- | ------------------------- | -------------------------- |
| Read       | Open a file               | List contents of directory |
| Write      | Change contents of a file | Create and delete files    |
| Execute    | Run a program file        | Change to the directory    |

### Applying The Permissions
To apply the above permissions, use `chmod`. There are two modes for chmod
1. Absolute Mode - Use digits. Not my favorite 
2. Relative Mode - Use letters. My favorite 😈

| **Permission** | **Numeric Representation** |
| ---------- | ---------------------- |
| Read       | 4                      |
| Write      | 2                      |
| Execute    | 1                      |


### Special Permissions 
| Permisison | Numeric Value | Relative Value | On Files                                            | On Directories                                       |
| ---------- | ------------- | -------------- | --------------------------------------------------- | ---------------------------------------------------- |
| SUID       | 4             | u+s            | User executes file with permissions of file owner.  A file with **SUID** always executes as the user who owns the file, regardless of the user passing the command.| n/A                                                  |
| SGID       | 2             | g+s            | User executes file with permissions of group owner. -   If set on a file, it allows the file to be executed as the **group** that owns the file (similar to SUID)|  If set on a directory, any files created in the directory will have their **group** ownership set to that of the directory owner |
| Sticky Bit | 1             | +t             | n/A                                                 | Prevents users from deleting files from other users.   Only the owner can delete files                                                  |