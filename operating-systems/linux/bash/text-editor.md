# Text editor

## nano

| Command    | Action                        |
| ---------- | ----------------------------- |
| `Ctrl + O` | Write (save) the current file |
| `Ctrl + X` | Exit Nano                     |
| `Ctrl + W` | Search text                   |
| `Ctrl + K` | Cut the current line          |
| `Ctrl + U` | Paste the cut line            |
| `Ctrl + G` | Display help                  |
| `Ctrl + C` | Show current cursor position  |
| `Ctrl + J` | Justify the current paragraph |
| `Ctrl + R` | Insert another file           |
| `Ctrl + Y` | Move one page up              |
| `Ctrl + V` | Move one page down            |
| `Ctrl + _` | Go to specific line number    |
| `Alt + A`  | Start selecting text (mark)   |
| `Ctrl + \` | Search and replace            |

***

## vim

#### Basic Vim Modes

* **Normal mode**: For navigation and commands (default mode)
* **Insert mode**: For typing text (`i` to enter insert mode)
* **Visual mode**: For selecting text (`v` to enter visual mode)

**Switching Modes**

| Command    | Action                  |
| ---------- | ----------------------- |
| `i`        | Enter Insert mode       |
| `Esc`      | Return to Normal mode   |
| `v`        | Enter Visual mode       |
| `V`        | Enter Visual Line mode  |
| `Ctrl + v` | Enter Visual Block mode |

**Basic Navigation (Normal mode)**

| Command | Action                    |
| ------- | ------------------------- |
| `h`     | Move left                 |
| `j`     | Move down                 |
| `k`     | Move up                   |
| `l`     | Move right                |
| `0`     | Move to beginning of line |
| `$`     | Move to end of line       |
| `gg`    | Go to beginning of file   |
| `G`     | Go to end of file         |
| `w`     | Move to next word         |
| `b`     | Move to previous word     |

**Editing Text**

| Command    | Action                            |
| ---------- | --------------------------------- |
| `i`        | Insert before cursor              |
| `a`        | Insert after cursor               |
| `o`        | Open a new line below and insert  |
| `O`        | Open a new line above and insert  |
| `x`        | Delete character under cursor     |
| `dd`       | Delete current line               |
| `dw`       | Delete from cursor to end of word |
| `D`        | Delete from cursor to end of line |
| `u`        | Undo                              |
| `Ctrl + r` | Redo                              |

**Copy, Cut, and Paste (Yank and Put)**

| Command | Action                    |
| ------- | ------------------------- |
| `yy`    | Yank (copy) current line  |
| `yw`    | Yank (copy) word          |
| `p`     | Paste after cursor        |
| `P`     | Paste before cursor       |
| `dd`    | Cut (delete) current line |

**Searching**

| Command | Action                                   |
| ------- | ---------------------------------------- |
| `/text` | Search forward for "text"                |
| `?text` | Search backward for "text"               |
| `n`     | Repeat last search in same direction     |
| `N`     | Repeat last search in opposite direction |
|         |                                          |

**Saving and Quitting**

| Command       | Action              |
| ------------- | ------------------- |
| `:w`          | Save file           |
| `:q`          | Quit Vim            |
| `:wq` or `:x` | Save and quit       |
| `:q!`         | Quit without saving |

**Useful Extras**

| Command         | Action                               |
| --------------- | ------------------------------------ |
| `.`             | Repeat last command                  |
| `:%s/old/new/g` | Replace all "old" with "new" in file |
| `:set number`   | Show line numbers                    |
| `:set nonumber` | Hide line numbers                    |
