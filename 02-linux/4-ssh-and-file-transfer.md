# SSH and File Transfer

This page contains my notes on remote access and file transfer methods in Linux.

---

## SSH — Secure Shell

SSH (Secure Shell) is a protocol used to securely connect to another computer or server over a network.

It provides an encrypted remote terminal session.

General syntax:

`ssh username@ip_address`

Example:

`ssh sammie@10.112.188.38`

Here:

- `ssh` → starts an SSH connection
- `sammie` → username on the remote system
- `10.112.188.38` → IP address of the remote system

---

## First SSH Connection

When connecting to a system for the first time, SSH may ask whether I trust the remote host.

After accepting the host key, the remote user's password is requested.

Once authenticated, the terminal prompt changes and I can execute commands on the remote machine.

---

## SSH with a Different Port

SSH normally uses port `22`.

If the SSH service runs on another port, the `-p` option can be used.

Example:

`ssh -p 2222 username@ip_address`

---

## Leaving an SSH Session

To disconnect from the remote system:

`exit`

This returns me to my local terminal.

---

# SCP — Secure Copy

SCP (Secure Copy Protocol) transfers files between systems using SSH.

Because it uses SSH, the connection is encrypted and authenticated.

The general structure is:

`scp SOURCE DESTINATION`

---

## Copying a Local File to a Remote System

Example:

`scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`

This means:

- Local file → `important.txt`
- Remote user → `ubuntu`
- Remote IP → `192.168.1.30`
- Destination → `/home/ubuntu/transferred.txt`

---

## Copying a Remote File to the Local System

Example:

`scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt`

This downloads the remote file and saves it locally as:

`notes.txt`

---

# `wget` — Downloading Files

`wget` can download files over HTTP or HTTPS.

Example:

`wget https://example.com/file.txt`

The downloaded file is normally saved in the current working directory.

---

## Downloading from a Specific Port

If a web server is running on a non-default port, the port must be included in the URL.

Example:

`wget http://10.114.137.188:8000/myfile`

Here:

- `10.114.137.188` → server IP
- `8000` → server port
- `myfile` → requested file

---

# Python HTTP Server

Python can quickly turn a directory into a simple HTTP server.

From the directory containing the files I want to share:

`python3 -m http.server`

By default, the server listens on port:

`8000`

Example output:

`Serving HTTP on 0.0.0.0 port 8000`

This means the files in the current directory are now available through HTTP.

---

## Downloading a File from the Python Server

If the server IP is:

`10.114.137.188`

and the file is:

`file`

another machine can download it with:

`wget http://10.114.137.188:8000/file`

---

## Why a Second Terminal Is Needed

When I run:

`python3 -m http.server`

the terminal remains occupied because the web server keeps running.

Therefore, I need to open another terminal to execute commands such as:

`wget`

The first terminal must remain running until the file transfer is finished.

---

# Common HTTP Server Errors

## Connection Refused

Example:

`Connection refused`

This usually means nothing is listening on the requested port.

For example, if I try:

`wget http://10.114.137.188:8000/file`

before starting the Python HTTP server, the connection can fail.

The server must first be started with:

`python3 -m http.server 8000`

---

## 404 File Not Found

Example:

`404 File not found`

This means the web server is running, but the requested file name or path does not exist.

For example, if the real file is:

`.flag.txt`

but I request:

`flag.txt`

the server cannot find it.

The correct request would be:

`wget http://10.114.137.188:8000/.flag.txt`

---

# Hidden Files and File Transfer

Linux files beginning with `.` are hidden.

Example:

`.flag.txt`

A normal:

`ls`

may not show the file.

To display hidden files:

`ls -a`

or:

`ls -la`

After finding the exact file name, it can be requested through HTTP.

---

# SSH vs SCP vs wget

| Tool | Purpose |
|---|---|
| `ssh` | Remote encrypted terminal access |
| `scp` | Secure file transfer using SSH |
| `wget` | Download files over HTTP/HTTPS |
| `python3 -m http.server` | Quickly serve files over HTTP |

---

# Typical Lab Workflow

A simple lab file-transfer workflow can look like this:

1. Connect to a remote Linux machine using SSH.
2. Locate the file I need.
3. Start a temporary HTTP server in the directory containing the file.
4. Keep that terminal running.
5. Open another terminal on the receiving machine.
6. Download the file using `wget`.

Example:

Server:

`python3 -m http.server 8000`

Client:

`wget http://SERVER_IP:8000/file.txt`

---

# Security Notes

SSH and SCP provide encrypted communication.

A basic Python HTTP server does not provide the same protection by default.

Because of this, temporary HTTP servers are useful in controlled lab environments, but sensitive real-world data should be transferred using secure methods.

---

# Quick Reference

| Command | Purpose |
|---|---|
| `ssh user@IP` | Connect to a remote system |
| `ssh -p PORT user@IP` | SSH using another port |
| `exit` | Leave SSH session |
| `scp file user@IP:/path/` | Upload a file |
| `scp user@IP:/file .` | Download a file |
| `wget URL` | Download a file |
| `python3 -m http.server` | Start HTTP server on port 8000 |
| `python3 -m http.server 8000` | Explicitly start on port 8000 |
| `ls -la` | Show hidden files |
