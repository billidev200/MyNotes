# Text Processing

## find

The `find` command in Linux is used to **search for files and directories** in a directory hierarchy. It's extremely powerful and flexible, allowing you to search by name, type, size, permissions, modification time, and more.

`*` mean all

```bash
find [path] [options] [expression]
```

**Specific file**

```bash
sudo find / -type f -name "filename.ext" 2>/dev/null
```

🔹 Explanation:

* `sudo` — Required to search protected directories.
* `/` — Start from the root directory (search entire filesystem).
* `-type f` — Look for files (not directories).
* `-name "filename.ext"` — Replace with the exact file name you're searching for.
* `2>/dev/null` — Suppresses permission-denied errors for cleaner output.

| Option                | Description                                          | Example                               |
| --------------------- | ---------------------------------------------------- | ------------------------------------- |
| `.`                   | Current directory (search from here)                 | `find .`                              |
| `-name "<pattern>"`   | Find files with a specific name (supports wildcards) | `find . -name "file.txt"`             |
| `-iname "<pattern>"`  | Case-insensitive name match                          | `find . -iname "*.jpg"`               |
| `-type f`             | Find files only                                      | `find . -type f`                      |
| `-type d`             | Find directories only                                | `find . -type d`                      |
| `-size +<n>[c/k/M/G]` | File size greater than n (c = bytes, k = KB, etc.)   | `find . -size +10M`                   |
| `-mtime -n`           | Modified in the last _n_ days                        | `find . -mtime -1`                    |
| `-atime -n`           | Accessed in the last _n_ days                        | `find . -atime -7`                    |
| `-perm <mode>`        | Find files with specific permissions                 | `find . -perm 644`                    |
| `-user <username>`    | Owned by user                                        | `find /home -user john`               |
| `-group <groupname>`  | Owned by group                                       | `find /data -group staff`             |
| `-exec <cmd> {} \;`   | Run a command on each result                         | `find . -name "*.log" -exec rm {} \;` |
| `-delete`             | Delete all matching files (use with care!)           | `find . -name "*.tmp" -delete`        |

🔹 Example Use Cases:

**Find all `.log` files and delete them**:

```bash
find /var/log -type f -name "*.log" -delete
```

**Find files larger than 100MB**:

```bash
find . -type f -size +100M
```

**Find files modified in the last 24 hours**:

```bash
find . -mtime -1
```

## grep

The `grep` command is used in Linux to **search for text patterns** inside files or command outputs. It's short for "**Global Regular Expression Print**" and is incredibly powerful for text processing and searching.

```bash
grep [options] "pattern" [file...]
```

| Option         | Description                                    | Example                         |
| -------------- | ---------------------------------------------- | ------------------------------- |
| `-i`           | Case-insensitive match                         | `grep -i "hello" file.txt`      |
| `-r` or `-R`   | Recursively search directories                 | `grep -r "main()" ./src`        |
| `-n`           | Show line numbers in results                   | `grep -n "error" log.txt`       |
| `-v`           | Invert match (show lines that **don’t** match) | `grep -v "success" results.txt` |
| `-l`           | List only filenames that contain a match       | `grep -l "password" *.php`      |
| `-c`           | Count number of matches per file               | `grep -c "404" access.log`      |
| `-w`           | Match whole words only                         | `grep -w "cat" animals.txt`     |
| `--color=auto` | Highlight matches in color                     | `grep --color=auto "TODO" *.py` |

**Find a word in a file:**

```bash
grep "hello" myfile.txt
```

**Search case-insensitively:**

```bash
grep -i "ubuntu" system.txt
```

**Find all `.log` files that mention "error":**

```bash
grep -l "error" *.log
```

The `| grep` part of a command is used to **filter the output of another command** using a **pipe (`|`)**, which sends the output of the first command **as input** to `grep`.

```bash
command | grep "pattern"
```

Filter with `grep` to Find Specific Scripts:

```bash
ls /usr/share/nmap/scripts/ | grep "http"
```

## awk

## shred

1. **Overwrites file contents** multiple times with patterns of data (random bytes, all zeros, all ones, etc.).
2. Optionally **renames** the file repeatedly to hide the original name.
3. Finally, it **truncates** (shrinks to zero size) and **removes** the file.

By default, `shred` does **three** overwrite passes plus a final pass of zeros, but you can change that.

## head

The `head` command is used to display the first part of files.

It's particularly useful for previewing the start of a file to understand its structure.

All examples below use the `logfile.txt` file:

The `head` command displays the first 10 lines of a file by default:

**Options**

The `head` command has several options used to customize its behavior:

* `-n [number]`: Display the first \[number] lines of the file.
* `-c [number]`: Display the first \[number] bytes of the file.

## tail

The `tail` command is used to display the last part of files.

It's particularly useful for viewing the end of log files or any file that is being updated in real-time.

The `tail` command has several options to customize its behavior:

* `-n [number]`: Display the last \[number] lines of the file.
* `-f`: Follow the file as it grows, useful for monitoring log files.
* `-c [number]`: Display the last \[number] bytes of the file.
* `--pid=[pid]`: Terminate after the process with the given PID dies.
* `--retry`: Keep trying to open a file even if it is inaccessible.

## cmp

compare files

```bash
diff file1.txt file2.txt
```

| Option      | Description                                |
| ----------- | ------------------------------------------ |
| `-l`        | Show all differing bytes                   |
| `-s`        | Silent mode (no output, just exit code)    |
| `-i N`      | Skip first N bytes of both files           |
| `-i N:M`    | Skip N bytes of FILE1 and M bytes of FILE2 |
| `-n N`      | Compare only first N bytes                 |
| `--help`    | Show help message                          |
| `--version` | Show version                               |

## diff

tell file diffrents

```bash
diff file1.txt file2.txt
```

| Option                    | Description                                   |
| ------------------------- | --------------------------------------------- |
| `-u`                      | Unified format (most common, used in patches) |
| `-c`                      | Context format                                |
| `--side-by-side` or `-y`  | Side-by-side comparison                       |
| `--suppress-common-lines` | Only show differences in side-by-side mode    |

## sort

The `sort` command is used to sort lines of text files.

It's a handy tool for organizing data in files.

**Options**

The `sort` command has options to change how it works:

* `-r` - Sort in reverse order
* `-n` - Sort numbers correctly
* `-k` - Sort by a specific column
* `-u` - Remove duplicate lines
* `-t` - Specify a delimiter for fiel
