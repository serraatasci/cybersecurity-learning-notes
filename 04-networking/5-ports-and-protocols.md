# Ports and Common Network Protocols

This page contains my notes on network ports and several common protocols that appear frequently in cybersecurity labs.

---

## What Is a Port?

A port helps identify which network service or application should receive traffic on a computer.

A single server can run multiple services at the same time.

For example:

`Server IP`

↓

`Different Ports`

↓

`Different Services`

Conceptually:

`IP Address = Which device?`

`Port = Which service on that device?`

---

# Service and Port Relationship

A network service usually listens on a specific port.

For example:

- SSH commonly uses port `22`
- FTP commonly uses port `21`
- HTTP commonly uses port `80`
- HTTPS commonly uses port `443`
- Telnet commonly uses port `23`

These are common default ports.

A service can technically be configured to use another port.

---

# Common Ports

| Protocol | Common Port | Purpose |
|---|---:|---|
| FTP | 21 | File transfer |
| SSH | 22 | Secure remote terminal |
| Telnet | 23 | Remote terminal |
| HTTP | 80 | Web communication |
| HTTPS | 443 | Encrypted web communication |

---

# FTP — File Transfer Protocol

FTP stands for:

`File Transfer Protocol`

FTP is used to transfer files between systems.

A client can connect to an FTP server and perform actions such as:

- View files
- Download files
- Upload files, if permitted

---

## FTP Login

An FTP server may require:

- Username
- Password

In some lab environments, FTP may also allow:

`Anonymous Login`

This means a user can connect without having a normal personal account.

---

# Anonymous FTP

Anonymous FTP allows users to access files without standard user credentials.

In security testing, an FTP server that allows anonymous access should be reviewed carefully.

The important question is:

`What files can an unauthenticated user access?`

Anonymous FTP is not automatically a vulnerability, but misconfiguration can expose sensitive files.

---

# FTP Security

FTP does not provide the same encrypted communication as SSH-based protocols.

This is important because authentication information and transferred data may not be protected in the same way as encrypted protocols.

A simple way to remember:

`FTP = File transfer`

but:

`Not designed as encrypted secure remote communication`

---

# SSH — Secure Shell

SSH stands for:

`Secure Shell`

SSH is used for secure remote command-line access.

Common port:

`22`

Example connection format:

`ssh username@ip_address`

SSH provides an encrypted connection between the client and remote system.

---

## What Can SSH Be Used For?

SSH can be used for:

- Remote terminal access
- System administration
- Executing commands remotely
- Secure file transfer through related tools such as SCP

---

# Telnet

Telnet is another protocol used for remote terminal access.

Common port:

`23`

Like SSH, it allows a user to interact with a remote computer through a terminal.

However, there is an important security difference.

---

# Telnet vs SSH

The main difference from my notes is:

`Telnet`

→ Communication is not encrypted

`SSH`

→ Communication is encrypted

This makes SSH the safer choice for remote administration.

---

## Simple Comparison

| Telnet | SSH |
|---|---|
| Remote terminal | Remote terminal |
| Common port 23 | Common port 22 |
| Unencrypted communication | Encrypted communication |
| Older protocol | Preferred for secure remote access |

The easiest way to remember:

`Telnet = Remote terminal without encryption`

`SSH = Secure encrypted remote terminal`

---

# HTTP

HTTP stands for:

`Hypertext Transfer Protocol`

HTTP is commonly used for communication between:

`Web Browser`

and:

`Web Server`

Common port:

`80`

Simplified:

`Browser`

↓

`HTTP Request`

↓

`Web Server`

↓

`HTTP Response`

---

# HTTPS

HTTPS is the encrypted version of HTTP.

Common port:

`443`

The important difference is:

`HTTP`

→ Web communication without HTTPS encryption

`HTTPS`

→ Encrypted web communication

---

# HTTP vs HTTPS

| HTTP | HTTPS |
|---|---|
| Common port 80 | Common port 443 |
| Web communication | Web communication |
| Not encrypted in the same way | Encrypted communication |

A simple way to remember:

`HTTPS = HTTP + Encryption`

---

# Why HTTPS Matters

When web communication is encrypted, other devices on the network should not normally be able to simply read the application data as plain text.

This helps protect information such as:

- Login credentials
- Session information
- Personal information
- Web traffic contents

---

# Services and Version Information

During cybersecurity labs, identifying only the open port is not always enough.

It can also be useful to identify:

- Which service is running
- Which software version is running

For example:

`Port 21`

may indicate FTP.

But the exact FTP server software and version can provide more information about the system.

This is one reason service detection is useful during authorized network reconnaissance.

---

# Old Software Versions

The notes also emphasize checking service versions for known weaknesses.

The general idea is:

`Service`

↓

`Version`

↓

`Known vulnerability?`

An outdated network service may have publicly known security problems.

This is why keeping network-facing services updated is important.

---

# Protocol vs Service

These terms are closely related but not identical.

A:

`Protocol`

defines communication rules.

A:

`Service`

is the software functionality available through the network.

For example:

`FTP`

is the protocol.

An FTP server application provides the FTP service.

---

# Ports and Cybersecurity

Ports help security analysts understand what network services are exposed by a system.

For example:

`22 open`

may indicate SSH.

`21 open`

may indicate FTP.

`80 open`

may indicate a web server.

But the port number alone should not always be treated as proof of the exact service.

Services can be configured on non-standard ports.

---

# Basic Investigation Logic

A simple network-service workflow is:

1. Identify the target
2. Identify open ports
3. Identify the services
4. Identify service versions
5. Understand what each service does
6. Review whether the service is securely configured

This creates a more complete picture of the target system.

---

# Secure vs Insecure Protocol Examples

From the protocols covered in my notes:

`Telnet`

→ Unencrypted remote terminal

`SSH`

→ Encrypted remote terminal

and:

`HTTP`

→ Basic web communication

`HTTPS`

→ Encrypted web communication

This shows why protocol selection matters in security.

---

# Quick Reference

| Term | Meaning |
|---|---|
| Port | Identifies a network service/application |
| FTP | File Transfer Protocol |
| SSH | Secure Shell |
| Telnet | Remote terminal protocol |
| HTTP | Hypertext Transfer Protocol |
| HTTPS | Encrypted HTTP communication |
| Port 21 | Common FTP port |
| Port 22 | Common SSH port |
| Port 23 | Common Telnet port |
| Port 80 | Common HTTP port |
| Port 443 | Common HTTPS port |
| Anonymous FTP | FTP access without a normal user account |
| Service Version | Version of software providing a network service |

---

## Key Takeaway

The easiest way to remember ports is:

`IP Address = Which computer?`

`Port = Which service?`

Important examples from my notes are:

`21 → FTP`

`22 → SSH`

`23 → Telnet`

`80 → HTTP`

`443 → HTTPS`

And the important security comparisons are:

`SSH > Telnet for secure remote access`

`HTTPS > HTTP for encrypted web communication`
