# Hydra

## THC Hydra Basic Syntax

```bash
hydra [options] [target] [module]
```

## Modules

| Module name      | Service / Protocol                          |
| ---------------- | ------------------------------------------- |
| `ssh`            | Secure Shell login                          |
| `ftp`            | File Transfer Protocol                      |
| `http-get`       | HTTP GET request authentication             |
| `http-post-form` | HTTP POST form-based login                  |
| `smtp`           | Simple Mail Transfer Protocol login         |
| `pop3`           | Post Office Protocol                        |
| `imap`           | Internet Message Access Protocol            |
| `rdp`            | Remote Desktop Protocol                     |
| `smb`            | Server Message Block (Windows file sharing) |
| `telnet`         | Telnet login                                |
| `mysql`          | MySQL database login                        |

## Commands

| Option      | Description                                                           |
| ----------- | --------------------------------------------------------------------- |
| `-l USER`   | Single username                                                       |
| `-L FILE`   | File with list of usernames                                           |
| `-p PASS`   | Single password                                                       |
| `-P FILE`   | File with list of passwords                                           |
| `-s PORT`   | Specify port number (default depends on module)                       |
| `-t TASKS`  | Number of parallel connections (default: 16)                          |
| `-w TIME`   | Timeout for responses (in seconds)                                    |
| `-v`        | Verbose mode (shows attempts)                                         |
| `-V`        | Very verbose (shows each password tried)                              |
| `-e ns`     | Enable additional checks: n = null password, s = username as password |
| `-f`        | Exit after first found login/password combo                           |
| `-m FILE`   | Specify module list file                                              |
| `-M FILE`   | File with list of target hosts (for multiple)                         |
| `-o FILE`   | Write found login/password pairs to file                              |
| `-O`        | Use uppercase for output file                                         |
| `-R`        | Restore a previous session                                            |
| `-S`        | Use SSL / TLS if supported                                            |
| `-I`        | Ignore an invalid login/password (don't retry)                        |
| `-b FORMAT` | Specify output format (e.g. hydra, json)                              |
