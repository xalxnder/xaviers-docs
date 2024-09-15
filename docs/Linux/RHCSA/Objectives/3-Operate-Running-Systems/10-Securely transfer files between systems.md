### Securely Transferring Files

To transfer files, you can use, `scp`, `rsync`, or `sftp`.

#### SCP
**Copy the /etc/hosts file to the /tmp directory on server2**
`scp /etc/hosts server2: /tmp`

**Copy an entire subdirectory.** 
`scp -r server2:/etc/ /tmp`

#### SFTP

#### RSYNC
The rsync command uses SSH to synchronize files between a remote directory and a local directory. The advantage of synchronizing files is that only differences need to be considered. So, for example, if you synchronize a 100-MiB file in which only a few blocks have changed since the previous sync, only the changed blocks will be synchronized. This approach is also known as a delta sync.