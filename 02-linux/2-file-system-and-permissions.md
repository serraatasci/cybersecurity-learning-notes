# Linux File System and Permissions

This page contains my notes on the Linux file system structure, users, groups, and file permissions.

---

## Linux File System Structure

Linux uses a hierarchical file system that starts from the root directory:

`/`

Important directories include:

### `/bin`

Contains essential user commands and binaries.

Examples:

`ls`

`cat`

`cp`

`mv`

---

### `/sbin`

Contains system administration binaries.

These commands are generally used for system-level tasks and are often associated with the root user.

---

### `/etc`

Contains system configuration files.

Examples include:

`/etc/passwd`

`/etc/shadow`

`/etc/sudoers`

Many Linux services and applications store their configuration files under `/etc`.

---

### `/var`

Stores variable data that changes frequently.

Examples:

- Logs
- Cache files
- Web server data
- Application data

A particularly important directory is:

`/var/log`

which stores system and service logs.

---

### `/tmp`

Stores temporary files.

Many users can write to this directory.

Because of this, `/tmp` is often useful during system administration and controlled cybersecurity labs.

Its contents may be removed after a reboot.

---

### `/home`

Contains normal users' home directories.

Example:

`/home/serra`

A user's personal files, documents, downloads, and configuration files are usually stored here.

---

### `/root`

This is the home directory of the root user.

It is different from:

`/home/root`

The root user's home directory is normally:

`/root`

---

### `/dev`

Contains files representing devices.

Linux treats many devices as files.

Examples may include:

- Disks
- Terminals
- USB devices

---

### `/mnt`

Often used as a temporary mount point for file systems.

---

### `/media`

Often used for removable media such as USB drives.

---

### `/srv`

May contain data used by services.

---

# Important Files in `/etc`

## `/etc/passwd`

Contains information about local user accounts.

It does not normally store plain-text passwords.

---

## `/etc/shadow`

Contains password-related information in protected form.

Access is restricted because it contains sensitive authentication data.

---

## `/etc/sudoers`

Controls which users or groups are allowed to execute commands with elevated privileges using `sudo`.

---

# Users and Groups

Linux permissions are based heavily on users and groups.

A file can have:

- An owner
- A group
- Permissions for everyone else

This allows access to be controlled in a detailed way.

---

## Switching Users

The `su` command can be used to switch to another user.

Example:

`su user2`

If a password is required, the password of the target user is entered.

Using:

`su -l user2`

starts a login shell that more closely resembles a normal login session for that user.

This usually changes environment variables and moves into the target user's home directory.

---

## Root User

The root user has very high privileges on the Linux system.

Commands executed as root can make critical system changes.

Because of this, root access should be used carefully.

---

# Understanding Linux Permissions

Linux file permissions commonly look like this:

`rwxr-xr-x`

These permissions are divided into three groups:

`rwx | r-x | r-x`

They represent:

1. Owner
2. Group
3. Others

---

## Permission Letters

### `r` — Read

Allows reading the contents of a file.

---

### `w` — Write

Allows modifying the file.

---

### `x` — Execute

Allows executing the file as a program or script.

For directories, execute permission also affects whether a user can enter or access items inside the directory.

---

# Viewing Permissions

The command:

`ls -l`

shows detailed file information.

Example:

`-rw-r--r-- 1 user user 120 notes.txt`

The first part:

`-rw-r--r--`

contains the file type and permissions.

---

## File Type Character

The first character indicates the file type.

Examples:

`-` → Regular file

`d` → Directory

After that, the permission groups follow.

Example:

`drwxr-xr-x`

This means:

- `d` → Directory
- `rwx` → Owner permissions
- `r-x` → Group permissions
- `r-x` → Others permissions

---

# Numeric Permission Values

Linux permissions can also be represented numerically.

Each permission has a value:

| Permission | Value |
|---|---|
| Read (`r`) | 4 |
| Write (`w`) | 2 |
| Execute (`x`) | 1 |

The values are added together for each permission group.

---

## Example: `777`

`rwxrwxrwx`

Calculation:

Owner:

`4 + 2 + 1 = 7`

Group:

`4 + 2 + 1 = 7`

Others:

`4 + 2 + 1 = 7`

Therefore:

`rwxrwxrwx = 777`

---

## Example: `755`

`rwxr-xr-x`

Owner:

`rwx = 7`

Group:

`r-x = 5`

Others:

`r-x = 5`

Therefore:

`755`

The owner has full permissions, while the group and others can read and execute.

---

## Example: `644`

`rw-r--r--`

Owner:

`rw- = 6`

Group:

`r-- = 4`

Others:

`r-- = 4`

Therefore:

`644`

The owner can read and write, while everyone else can only read.

---

## Example: `700`

`rwx------`

Only the owner has access.

---

# Changing Permissions with `chmod`

The `chmod` command changes file permissions.

Example:

`chmod 755 file`

This gives:

- Owner → read, write, execute
- Group → read, execute
- Others → read, execute

Another example:

`chmod 750 system_overview.txt`

This means:

- Owner → full access
- Group → read and execute
- Others → no access

---

# Why Permissions Matter in Cybersecurity

Incorrect permissions can expose sensitive information or allow unauthorized changes.

Examples include:

- Password files readable by unauthorized users
- Scripts writable by everyone
- Sensitive configuration files exposed to normal users
- Executable files with excessive permissions

Understanding permissions helps identify security weaknesses and control access to important files.

---

# Quick Reference

| Item | Meaning |
|---|---|
| `/etc` | System configuration |
| `/var` | Variable data and logs |
| `/tmp` | Temporary files |
| `/home` | User home directories |
| `/root` | Root user's home directory |
| `/dev` | Device files |
| `r` | Read |
| `w` | Write |
| `x` | Execute |
| `755` | Owner full, others read/execute |
| `644` | Owner read/write, others read |
| `700` | Owner only |
| `chmod` | Change permissions |
| `su` | Switch user |
