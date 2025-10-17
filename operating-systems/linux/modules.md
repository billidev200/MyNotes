# Modules

## du

is a command in linux (short for disk usage) which helps you identify what files/directories are consuming how much space. If you run a simple du command in terminal.

Important flags

| Flag         | Description                                                                                                           |
| ------------ | --------------------------------------------------------------------------------------------------------------------- |
| -a           | Will list files as well with the folder.                                                                              |
| -h           | Will list the file sizes in human readable format(B,MB,KB,GB)                                                         |
| -c           | Using this flag will print the total size at the end. Jic you want to find the size of directory you were enumerating |
| -d \<number> | Flag to specify the depth-ness of a directory you want to view the results for (eg. -d 2)                             |
| --time       | To get the results with time stamp of last modified.                                                                  |

## Grep, Egrep, Fgrep

Introduction

It is a must known tool to everyone and that's why linux modules won't be complete without doing a mention of its amazing charisma. This tool, is what filters the good output we need from the residue. The official documentation says, The grep filter searches a file for a particular pattern of characters, and displays all lines that contain that pattern. The pattern that is searched in the file is referred to as the regular expression. The pattern is what I am gonna brief you about.

Syntax: `grep "PATTERN" file.txt` will search the file.txt for the specified "PATTERN" string, if the string is found in the line, the grep will return the whole line containing the "PATTERN" string.&#x20;

The Family Tree

egrep and fgrep are no different from grep(other than 2 flags that can be used with grep to function as both). In simple words, egrep matches the regular expressions in a string, and fgrep searches for a fixed string inside text. Now grep can do both their jobs by using -E and -F flag, respectively.

In other terms, `grep -E` functions same as `egrep` and `grep -F` functions same as `fgrep`.

Important Flags

| Flags | Description                                                                                                                                                                               |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -R    | Does a recursive grep search for the files inside the folders(if found in the specified path for pattern search; else grep won't traverse diretory for searching the pattern you specify) |
| -h    | If you're grepping recursively in a directory, this flag disables the prefixing of filenames in the results.                                                                              |
| -c    | This flag won't list you the pattern only list an integer value, that how many times the pattern was found in the file/folder.                                                            |
| -i    | I prefer to use this flag most of the time, this is what specifies grep to search for the PATTERN while IGNORING the case                                                                 |
| -l    | will only list the filename instead of pattern found in it.                                                                                                                               |
| -n    | It will list the lines with their line number in the file containing the pattern.                                                                                                         |
| -v    | This flag prints all the lines that are NOT containing the pattern                                                                                                                        |
| -E    | This flag we already read above... will consider the PATTERN as a regular expression to find the matching strings.                                                                        |
| -e    | The official documentation says, it can be used to specify multiple patterns and if any string matches with the pattern(s) it will list it.                                               |

You might be wondering the difference between -E and -e flag. I suggest to understand this as the following:

* -e flag can be used to specify multiple patterns, with multiple use of -e flag( grep -e PATTERN1 -e PATTERN2 -e PATTERN3 file.txt), whereas, -E can be used to specify one single pattern(You can't use -E multiple times within a single grep statement).

Other point that you can use to understand the difference is, -e works on the BREs(Basic Regular Expressions) and -E works on EREs (Extended Regular Expressions).

* BREs tend to match a single pattern in a file (Simplest examples can be direct words like "sun", "comic")
* EREs tend to match 2 or more patterns in a file (To select a no of words like (sun sunyon sandston) the pattern could be "^s.\*n$").&#x20;

## STROPS

String Manipulations (STRing OPerationS)

Many people discard this topic in their tutorials/courses, which I believe is leaving behind the true power of linux and it's terminal interface. You ever see someone typing a very long command piping their outputs into some other commands? Well believe me when I say, you can select a single byte character from a GB long array of string bytes, if you could master that.&#x20;

If you're from a programming background you might have used indexing in arrays, slicing in python, or even grepping in terminal... All are a means of string manipulations. Especially in bash, we have a TON of tools to perform a same kind of operation, with different flags or string patterns specified, but obviously we will be choosing the one, providing us the shortest and easiest syntax possible.&#x20;

For strops, we have the following tools that I always keep in my arsenal and you should too:

* tr
* awk
* sed
* xargs

Other commands to be familiar with:

* sort
* uniq

## tr

Syntax: `tr [flags] [source]/[find]/[select] [destination]/[replace]/[change]`

| Flags | Description                                                                                                                                                                                                                                                 |
| ----- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -d    | To delete a given set of characters                                                                                                                                                                                                                         |
| -t    | To concat source set with destination set(destination set comes first; t stands for truncate)                                                                                                                                                               |
| -s    | To replace the source set with the destination set(s stands for squeeze)                                                                                                                                                                                    |
| -c    | This is the REVERSE card in this game, for eg. If you specify -c with -d to delete a set of characters then it will delete the rest of the characters leaving the source set which we specified (c stands for complement; as in doing reverse of something) |
