unix_users
==========

Creates or removes UNIX users ans groups.

Requirements
------------

None.

Role Variables
--------------

`_unix_users` is used to define users to add or remove.

`_unix_users.users[ ].state` may be set to `present` to create and maintain or to `absent` to remove a user.

Dependencies
------------

None.

Example Playbook
----------------

```
    - hosts: servers
      vars:
        UNIX_USERS:
          groups:
            - { name: admin, system: yes }
          sudo:
            group: admin
          users:
            - name: user.name
              state: present
              comment: User Name
              password:
              ssh:
                public_key: ssh-rsa ##INVALID KEY - PLEASE USE REAL PUBLIC KEY
              shell: /usr/bin/zsh
              groups:
                - admin
      roles:
        - { role: unix_users, tags: [ 'unix_users' ], _unix_users: "{{ UNIX_USERS }}" }
```

License
-------

See LICENSE file.

Author Information
------------------

Initially created by Lukas Pustina [@drivebytesting](https://twitter.com/drivebytesting).

