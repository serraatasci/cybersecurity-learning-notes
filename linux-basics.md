# Linux Basics

## Before Removing Wi-Fi Adapter

Before removing the external Wi-Fi adapter, the wireless interface should be stopped and the NetworkManager service can be restarted.

Commands:
- airmon-ng stop <interface>
- ip link set <interface> down
- systemctl restart NetworkManager

Replace <interface> with the correct wireless interface name such as wlan0 or wlan1.

## Keyboard Layout

setxkbmap tr = Changes the keyboard layout to Turkish.

## Basic Linux Commands

pwd = Prints the current working directory.

ls = Lists files and directories in the current directory.

cd <directory-name> = Changes the current directory.

cd .. = Moves one directory back.

mkdir <directory-name> = Creates a new directory.

clear = Clears the terminal screen.

touch notes.txt = Creates a new empty file.

cp notes.txt test/notes.txt = Copies a file from one location to another.

mv notes.txt test/notes.txt = Moves or renames a file.

rm notes.txt = Removes a file.

rm -r <directory-name> = Removes a directory and its contents.

Note: Commands such as rm -rf should be used very carefully because they can permanently delete files.

## User Privileges

sudo su = Switches to the superuser/root account.

exit = Exits from the current user session and returns to the previous user.

## Reading and Editing Files

cat notes.txt = Displays the content of a file.

nano notes.txt = Opens a file in the Nano text editor.

## File Information and Permissions

ls -la = Shows detailed information about files and directories.

Example output includes:
- File type and permissions
- Number of links
- Owner
- Group
- File size
- Last modification time
- File or directory name

Permission types:
- r = read
- w = write
- x = execute

## Network Information

ifconfig = Shows local IP and network interface information.

## Password Management

passwd = Changes the user password.
