When configuring local repos, I received the following error.
```
- Curl error (37): Couldn't read a file:// file for file:///repo/rhel9.iso/repodata/repomd.xml 
# Cant remember the exact output, but it was very similar to this
```


When configuring a repository from the installation disk, you'll need to create a mount location/directory. When editing the contents of that .repo file, ensure that the directory you created matches the {path} in `baseurl`=file:///{path}/{repo-name}.

So if your directory is `test_dir`, your baseurl will be `baseurl=file:///test_dir/AppStream`

#linux #repos #baseurl