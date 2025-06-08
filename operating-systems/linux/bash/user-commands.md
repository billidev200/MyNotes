# User commands

## useradd

| Option         | Description                                                         |
| -------------- | ------------------------------------------------------------------- |
| `-m`           | Create the user's home directory                                    |
| `-M`           | Do **not** create home dir (default on some distros)                |
| `-d DIR`       | Use DIR as home directory                                           |
| `-s SHELL`     | Set login shell (e.g., `/bin/bash`, `/bin/sh`)                      |
| `-g GROUP`     | Set the **primary** group                                           |
| `-G GROUPS`    | Set **supplementary** group(s), comma-separated                     |
| `-u UID`       | Set user ID                                                         |
| `-c COMMENT`   | Add a comment (e.g., full name)                                     |
| `-e DATE`      | Account expiration date (`YYYY-MM-DD`)                              |
| `-f DAYS`      | Inactive days after password expires before account is disabled     |
| `-r`           | Create a system account (non-login, e.g., for daemons)              |
| `-k SKELDIR`   | Specify an alternate skeleton directory (for copying default files) |
| `-p ENCRYPTED` | Set an already **encrypted** password (not plaintext)               |
| `-Z`           | Set SELinux user for the login (if applicable)                      |

## su

change user

```bash
su austin
```

| Option                           | Description                                                                            |
| -------------------------------- | -------------------------------------------------------------------------------------- |
| `-` or `-l`                      | Simulates a full login shell (loads target user’s `.bash_profile`, etc.)               |
| `-c 'COMMAND'`                   | Runs the specified command as the target user                                          |
| `-s SHELL`                       | Use a different shell instead of the default                                           |
| `-m` or `--preserve-environment` | Keep the current environment variables                                                 |
| `-p`                             | Similar to `-m`, preserves environment (especially `HOME`, `SHELL`, `USER`, `LOGNAME`) |

## exit

exit user

## passwd

change user password
