# Linux Basics

This page contains my notes on basic Linux command-line usage and shell fundamentals.

---

## Navigation Commands

### `pwd` — Print Working Directory

Shows the full path of the directory I am currently in.

Example:

`pwd`

Output example:

`/home/ubuntu/Documents`

---

### `ls` — List Directory Contents

Lists files and directories in the current location.

Basic usage:

`ls`

Useful options:

`ls -a`

Shows hidden files.

`ls -l`

Shows detailed information such as permissions, owner, group, size, and modification time.

`ls -lh`

Displays file sizes in a more human-readable format.

---

### `cd` — Change Directory

Moves between directories.

Example:

`cd Documents`

Go back one directory:

`cd ..`

Go directly to a specific path:

`cd /home/ubuntu/Documents`

---

## Viewing Files

### `cat`

Displays the contents of a file.

Example:

`cat notes.txt`

A full path can also be used:

`cat /home/ubuntu/Documents/notes.txt`

---

## Creating Files and Directories

### `touch`

Creates an empty file.

Example:

`touch notes.txt`

### `mkdir`

Creates a new directory.

Example:

`mkdir projects`

---

## Copying and Moving

### `cp` — Copy

Copies a file.

Example:

`cp notes.txt notes-copy.txt`

Copy a file to another directory:

`cp notes.txt Documents/`

---

### `mv` — Move / Rename

Moves a file:

`mv notes.txt Documents/`

It can also rename files:

`mv notes.txt new-notes.txt`

---

## Removing Files and Directories

### `rm`

Removes a file.

Example:

`rm notes.txt`

Remove a directory recursively:

`rm -R directory`

`rm` should be used carefully because deleted files are not normally moved to a recycle bin.

---

## Identifying File Types

### `file`

Determines the actual type of a file.

Example:

`file notes.txt`

Example output:

`notes.txt: ASCII text`

This is useful because file extensions are not always reliable.

---

## Clearing the Terminal

`clear`

Clears the terminal screen.

---

# Command Options and Help

Linux commands often support options or flags.

Example:

`ls -a`

Here:

- `ls` = command
- `-a` = option

Many commands provide built-in help:

`ls --help`

For more detailed documentation, Linux provides manual pages.

`man ls`

To exit a manual page:

`q`

---

# Shell Operators

## `&` — Run in Background

Runs a command in the background so the terminal can still be used.

General structure:

`command &`

---

## `&&` — Run the Next Command if the First Succeeds

General structure:

`command1 && command2`

`command2` only runs if `command1` completes successfully.

---

## `>` — Redirect Output

Sends command output into a file.

Example:

`echo hello > welcome.txt`

If the file already exists, its previous contents are overwritten.

---

## `>>` — Append Output

Adds output to the end of a file without deleting existing content.

Example:

`echo world >> welcome.txt`

---

## `|` — Pipe

Sends the output of one command to another command.

General structure:

`command1 | command2`

This is useful for chaining tools together.

---

# Terminal Text Editors

## Nano

Open or create a file:

`nano notes.txt`

Useful shortcuts:

- `Ctrl + O` → Save
- `Ctrl + X` → Exit
- `Ctrl + W` → Search

---

## Vim

Vim is a more advanced terminal text editor.

It supports features such as:

- Syntax highlighting
- Advanced navigation
- Custom keyboard shortcuts
- Powerful text editing

For beginner-level Linux work, Nano is generally easier to use.

---

# Quick Reference

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `cat` | Display file contents |
| `touch` | Create an empty file |
| `mkdir` | Create a directory |
| `cp` | Copy files |
| `mv` | Move or rename files |
| `rm` | Remove files |
| `file` | Identify file type |
| `clear` | Clear terminal |
| `man` | Open a manual page |
| `nano` | Edit text files |
