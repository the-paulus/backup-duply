Backup Duply
=========

Installs and configures duplicity and duply to perform scheduled backups.

Requirements
------------



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
      pre: >
        WORKDIR="/tmp"
      post: >
        WORKDIR="/tmp"
      cron_job:
        task: "backup"
        day: "*"
        hour: "0"
        minute: "0"
        month: "*"
        weekday: "*"
```

Dependencies
------------

None

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
