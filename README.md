Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

```yml
backup_duply_profiles:
  - home:
      gpg_key: "GPG_KEY_ID"
      gpg_pw: "GPG_PASSWORD"
      gpg_keys_enc: "<pubkey1>,<pubkey2>"
      gpg_key_sign: "<privkey>"
      gpg_pw_sign: "<signpass>"
      gpg_opts: "--homedir ~/.duply"
      target: "/home"
      target_user: "backup"
      target_pass: "backuppassword"
      source: "/home"
      duply_precmd: "trickle -s -u 640 -d 5120"
      exclude_filename: ".duplicity-ignore"
      max_age: "1M"
      max_full_backups: 1
      max_fulls_with_incrementals: 1
      max_full_backup_age: "1M"
      volume_size: "1G"
      temp_dir: "/tmp"
      arch_dir: "/safe/location"
      options: ""
      excludes:
        - */.local/share/Trash
        - */Dropbox
```

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
