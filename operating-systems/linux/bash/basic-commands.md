# Basic commands

## ls

The `ls` command has a variety of options to customize its output:

* `-l` - Long listing format
* `-a` - Include hidden files
* `-h` - Human-readable sizes
* `-t` - Sort by modification time
* `-r` - Reverse order while sorting
* `-R` - List subdirectories recursively
* `-S` - Sort by file size
* `-1` - List one file per line
* `-d` - List directories themselves, not their contents
* `-F` - Append indicator (one of \*/=@|) to entries

## cd

The `cd` command supports several useful options for navigating directories:

* `cd ..`: Move up one directory level
* `cd ~`: Change to the home directory
* `cd -`: Switch to the previous directory
* `cd /`: Change to the root directory

## pwd

The `pwd` command supports a few options to customize its output:

* `-L`: Display the logical current working directory
* `-P`: Display the physical current working directory (without symbolic links)

## echo

The `echo` command has several options to customize its output:

* `-n` - Don't add a new line at the end
* `-e` - Allow special characters like `\n` for new lines
* `-E` - Don't allow special characters (default)

## cat

The `cat` command has options to change how it shows text:

* `-n` - Add numbers to each line
* `-b` - Add numbers only to lines with text
* `-s` - Remove extra empty lines
* `-v` - Show non-printing characters (except for tabs and end of line)

## cp

The `cp` command has options to change how it works:

* `-r` - Copy all files and folders inside a directory
* `-i` - Ask before replacing files
* `-u` - Copy only if the source is newer
* `-v` - Verbose mode, show files being copied

`cp [source] [dest]` — Copy files or directories

## mv

The `mv` command has several options to customize its behavior:

* `-i` - Ask before replacing files
* `-u` - Move only if the source is newer
* `-v` - Verbose mode, show files being moved

`mv [source] [dest]` — Move or rename files or directories

## rm/rmdir

The `rm` command has options to change how it works:

* `-r` - Delete a folder and everything inside it
* `-i` - Ask before deleting each file
* `-f` - Force delete without asking
* `-v` - Verbose mode, show files being removed

⚠️ Be Careful — `rm` is permanent

* Deleted files do **not** go to a trash bin.
* There's **no undo** unless you're using special file recovery tools.

## mkdir

The `mkdir` command has several options to customize its behavior:

* `-p` - Create parent directories as needed
* `-v` - Show a message for each created directory
* `-m` - Set file mode (permissions)

## touch

The `touch` command has options to change how it works:

* `-a` - Update only when the file was last read
* `-m` - Update only when the file was last changed
* `-t` - Set the timestamp to a specific time
* `-c` - Do not create any files

## man

The basic syntax of the `man` command is:

#### Example: Man Command Syntax

```bash
man ls
```

```bash
man grep
```

If you are using Git Bash for Windows, `man` is not supported. Instead, you can use `[command] --help` command. For example, `ls --help`

## whoami

Show current logged-in user

## id

Show user ID and group ID

##

