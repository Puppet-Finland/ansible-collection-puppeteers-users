# Ansible Collection - puppeteers.users

This collection contains various roles for managing (Linux) system users. The
roles support multiple operating systems usingOS-agnostic dictionaries in
defaults/main.yml (look
[here](https://gist.github.com/JM1/9363beeb9fb5055e054b5f64aea0a598#approach-using-os-agnostic-dictionaries-in-defaultsmainyml)
for technical details and rationale).

All variables have been prefixed to avoid accidental variable name collisions.
The syntax is the following:

* \<author\>\_\<collection\>\_\<role\>\_\<variable\>

For example:

* puppeteers_users_localusers_users

## Roles

### puppeteers.users.localusers

This role manages local Linux system admin users. To use just pass a dictionary
of users along with their SSH authorized keys:

```
puppeteers_users_localusers_users:
  - name: john
    password: '<password-hash>'
    authorized_key: '<ssh-key>'
  - name: jane
    password: '<password-hash>'
    authorized_key: '<ssh-key>'
```

To create a user without a password:

```
puppeteers_users_localusers:
  - name: devops
    password: '!'
    authorized_key: '<ssh-key>'
```

To change the default shell (/bin/bash) for a user:

```
  - name: snowflake
    password: '<password-hash>'
    authorized_key: '<ssh-key>'
    shell: '/bin/zsh'
```

To override the default admin group (e.g. sudo or wheel) use:

```
puppeteers_users_localusers_admingroup: admin
```
