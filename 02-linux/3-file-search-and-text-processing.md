# File Search and Text Processing

This page contains my notes on searching for files and finding specific information inside files on Linux.

---

## `find` — Searching for Files and Directories

The `find` command is used to search for files and directories.

It is especially useful when I know the name of a file but do not know exactly where it is stored.

Example:

`find -name passwords.txt`

Possible output:

`./folder1/passwords.txt`

This tells me that the file is located inside the `folder1` directory.

---

## Searching by File Extension

Wildcards can be used to search for multiple files.

For example, to find all `.txt` files:

`find -name "*.txt"`

Possible output:

`./folder1/passwords.txt`

`./Documents/todo.txt`

The `*` wildcard means:

"match any characters"

So:

`*.txt`

means:

"any file whose name ends with `.txt`"

---

## Searching from a Specific Directory

A search location can also be specified.

Example:

`find /home -name notes.txt`

This searches inside `/home` and its subdirectories.

---

# `grep` — Searching Inside Files

The `grep` command searches for specific text inside files.

This is useful when a file contains many lines and I only want to find entries related to a particular value.

Example:

`grep "81.143.211.90" access.log`

Possible output:

`81.143.211.90 - - [25/Mar/2021:11:17 +0000] "GET / HTTP/1.1" 200`

Instead of reading the entire log manually, `grep` returns only the lines containing the searched value.

---

## Why `grep` Is Useful in Cybersecurity

Logs can contain hundreds or thousands of entries.

Using `grep`, I can quickly search for things such as:

- IP addresses
- Usernames
- Error messages
- Failed login attempts
- Specific URLs
- Suspicious commands
- Configuration values

For example:

`grep "Failed password" auth.log`

could be used to search for failed login entries in a log file.

---

# Recursive Search with `grep`

Sometimes the information I am looking for may exist inside many files and subdirectories.

The recursive option allows `grep` to search through all of them.

Example:

`grep -R "PRETTY_NAME" /etc/`

This means:

- Search inside `/etc/`
- Search through its subdirectories
- Find every occurrence of `PRETTY_NAME`

Possible output:

`/etc/os-release:PRETTY_NAME="Ubuntu"`

The output also shows which file contained the result.

---

## Permission Errors During Recursive Searches

While searching system directories, I may see messages such as:

`Permission denied`

Example:

`grep: /etc/sudoers: Permission denied`

This means the current user does not have permission to read that file.

It does not necessarily mean the command failed completely. Other accessible files can still be searched.

---

# `wc` — Counting File Content

The `wc` command can count lines, words, and characters.

A useful option is:

`wc -l`

which counts lines.

Example:

`wc -l access.log`

Possible output:

`244 access.log`

This tells me that the file contains 244 lines.

---

# Combining Tools

Linux tools become more useful when they are combined.

For example:

`grep "Failed" auth.log | wc -l`

The first command searches for lines containing `Failed`.

The pipe (`|`) sends those results to:

`wc -l`

which counts them.

This can be used to quickly determine how many matching entries exist.

---

# Search Workflow Example

If I know the file name:

`find -name mission_brief.txt`

Then I can read it:

`cat ./Documents/archive/mission_brief.txt`

If I know the information but not the file:

`grep -R "important_value" /home/`

This allows me to search directly through file contents.

---

# `find` vs `grep`

The easiest way to remember the difference is:

`find` → searches for files and directories

`grep` → searches for text inside files

Example:

`find -name "*.log"`

means:

"Find log files."

While:

`grep "error" application.log`

means:

"Find lines containing `error` inside this file."

---

# Quick Reference

| Command | Purpose |
|---|---|
| `find -name file.txt` | Search for a file by name |
| `find -name "*.txt"` | Find files by extension |
| `find /path -name file` | Search from a specific path |
| `grep "text" file` | Search inside a file |
| `grep -R "text" /path/` | Search recursively through files |
| `wc -l file` | Count lines |
| `command1 \| command2` | Pass output from one command to another |

---

## Key Takeaway

`find` helps locate files.

`grep` helps locate information inside files.

Together, they are very useful for system administration, log analysis, and cybersecurity investigations.
