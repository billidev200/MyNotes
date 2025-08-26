# System/information

uptime

The `uptime` command is used to find out how long the system has been running.

It provides a quick overview of the system's performance, including:

* The current time
* How long the system has been up
* The number of users logged in
* The system load averages for the past 1, 5, and 15 minutes

## top

Show real-time running processes

## htop

Improved interactive process viewer (may need installation)

## df

The `df` command is used to report file system disk space usage.

It's a useful tool for checking available storage on your system.

The `df` command has options to change how it works:

* `-h` - Show sizes in human-readable format (e.g., KB, MB)
* `-a` - Show all file systems, even empty ones
* `-T` - Show the type of file system
* `-i` - Show inode usage
* `-P` - Use POSIX output format

## kill

The `kill` command has several options to customize its behavior:

* `-9`: Forcefully terminate a process.
* `-l`: List all signal names.
* `-s [signal]`: Specify a signal to send.
* `-p`: Print the process ID.

## pkill

**Kill a process by name:**

```bash
pkill firefox
```

**Kill a process by PID:**

```bash
pkill 1234
```

Alternative: Using `kill` or `killall`

* `kill PID` to send signals to a process by PID.
* `killall process_name` kills all processes matching the name.

## free

The `free` command is used to display the amount of free and used memory in the system.

It's useful for monitoring memory usage and managing system resources.

The `free` command has options to change how it works:

* `-h` - Show memory in human-readable format (e.g., KB, MB, GB)
* `-b` - Show memory in bytes
* `-k` - Show memory in kilobytes (KB)
* `-m` - Show memory in megabytes (MB)
* `-g` - Show memory in gigabytes (GB)
* `-s [interval]` - Continuously display memory usage at specified intervals
* `-t` - Display total memory

## ps

The `ps` command has options to change how it works:

* `-e` - Show all processes
* `-f` - Show detailed information
* `-u` - Show processes for a specific user
* `-a` - Show all processes with a terminal
* `-x` - Show processes without a terminal

## top

The `top` command has options to change how it works:

* `-d` - Set the time between updates
* `-p` - Monitor specific PIDs
* `-u` - Show tasks for a specific user
* `-n` - Set the number of iterations
* `-b` - Batch mode operation

## du

The `du` command has options to change how it works:

* `-h` - Show sizes in human-readable format (e.g., KB, MB)
* `-s` - Show only the total size for each item
* `-a` - Show sizes for all files, not just directories
* `-c` - Produce a grand total
* `--max-depth=N` - Limit the depth of directory traversal

## uname

```bash
uname [OPTIONS]
```

| Option | Description                               |
| ------ | ----------------------------------------- |
| `-a`   | Show **all** available system info        |
| `-s`   | Show kernel name (default output)         |
| `-n`   | Show network node hostname                |
| `-r`   | Show kernel release version               |
| `-v`   | Show kernel version                       |
| `-m`   | Show machine hardware name (architecture) |
| `-p`   | Show processor type (if available)        |
| `-i`   | Show hardware platform (if available)     |
| `-o`   | Show operating system                     |

## neofetch

better uname

## cal

shows calendar

## shutdown

Shutdowns system

```bash
sudo shutdown -h now
```

Shutdown after 10 minutes

```bash
sudo shutdown -h +10
```

Shutdown and reboot

```bash
sudo shutdown -r now
```

## reboot

Reboots system

## dpkg

List installed packages

```bash
dpkg -l
```

## adduser

```bash
zsudo adduser <username>
```

## hostname

The `hostname` command will return the hostname of the target machine. Although this value can easily be changed or have a relatively meaningless string (e.g. Ubuntu-3487340239), in some cases, it can provide information about the target system’s role within the corporate network (e.g. SQL-PROD-01 for a production SQL server).

## sudo -l

The target system may be configured to allow users to run some (or all) commands with root privileges.

## &#x20;Last

This command tell us what user logged in before `last`
