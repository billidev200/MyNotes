# Text Processing

## find

## grep

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
