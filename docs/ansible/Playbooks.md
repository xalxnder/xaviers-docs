They contain Plays (which are the basic unit of Ansible execution). This is both an ‘execution concept’ and how we describe the files on which `ansible-playbook` operates. Playbooks are written in YAML and are easy to read, write, share and understand.

Here's an example
```yaml
---
- name: deploy vsftpd
- #Identifier. Can be used for documentation, or in tasks/handlers.
  hosts: ansible2.example.com
  # The host to connect to
  tasks:
    - name: install vsftpd
      yum: name=vsftpd
      #yum module - -   Installs, upgrade, downgrades, removes, and lists packages and groups with the _yum_ package manager.
    - name: enable vsftpd
      service: name=vsftpd enabled=true
      #service module - Controls services on remote hosts. Supported init systems include BSD init, OpenRC, SysV, Solaris SMF,   systemd, upstart.
    - name: create readme
      copy:
      # copy module - -   Copy files to remote locations
        content: "WELCOME!"
        dest: /var/ftp/pub/README
        force: no
        mode: 0444
```