# Cybersecurity Learning Notes

This repository contains my cybersecurity learning notes, practical exercises, and hands-on lab documentation.

I created this repository to organize what I learn while studying cybersecurity and to document my practical progress across Linux, Windows, networking, Active Directory, and offensive security topics.

---

## Current Learning Areas

### Linux

- Linux command-line fundamentals
- File system structure
- Users and permissions
- File searching and text processing
- SSH and file transfer
- Package management
- Cron and automation
- Log analysis

→ `02-linux/`

---

### Windows

- Windows file system and NTFS
- User accounts and profiles
- User Account Control (UAC)
- Windows administration tools
- Event Viewer
- Task Scheduler
- Services
- Windows Registry
- Windows Update
- Microsoft Defender
- Windows Firewall
- BitLocker
- TPM
- VSS

→ `03-windows/`

---

### Networking

- IP addresses
- DNS
- MAC addresses
- Network interfaces
- ARP
- Ports and protocols
- Network discovery
- Nmap
- VPN basics

→ `04-networking/`

---

### Active Directory

- Windows domains
- Domain Controllers
- Users and computer accounts
- Security Groups
- Organizational Units
- Delegation
- Principle of Least Privilege
- Group Policy Objects
- Kerberos
- NetNTLM
- Trees and forests
- Trust relationships

→ `05-active-directory/`

---

### Network Security

- Wireless security
- Monitor Mode
- Wireless traffic analysis
- ARP spoofing concepts
- Man-in-the-Middle concepts
- Traffic sniffing
- HTTPS
- HSTS

→ `06-network-security/`

---

### Offensive Security

- Reconnaissance
- Enumeration
- Nmap scanning
- Service detection
- Version detection
- CTF environments
- Metasploitable
- Basic service analysis

→ `07-offensive-security/`

---

# Hands-On Practice

In addition to theoretical notes, I document practical exercises performed in controlled cybersecurity environments.

Some of the topics I have practiced include:

- Active Directory OU management
- Delegating administrative permissions
- Password reset administration with PowerShell
- Group Policy configuration
- Domain authentication
- Linux system administration
- SSH and file transfer
- Network discovery
- Nmap service enumeration
- Wireless monitoring concepts
- Network traffic analysis

→ `08-labs/`

---

# Featured Lab — Active Directory Administration

One of my hands-on labs involved managing an Active Directory environment.

The lab included:

1. Reviewing the existing OU structure
2. Removing an outdated Organizational Unit
3. Handling accidental deletion protection
4. Delegating password reset permission to an IT Support user
5. Applying the Principle of Least Privilege
6. Testing the delegated permission using the assigned account
7. Resetting a domain user's password with PowerShell
8. Troubleshooting permission errors
9. Observing domain password policy enforcement
10. Validating the result through domain authentication

This lab helped me understand the relationship between:

`Identity → Permission → Delegation → Authentication → Validation`

Full write-up:

`05-active-directory/hands-on-administration-lab.md`

---

# Repository Structure

`01-fundamentals/`

General cybersecurity fundamentals.

`02-linux/`

Linux administration and security fundamentals.

`03-windows/`

Windows administration and built-in security features.

`04-networking/`

Networking fundamentals and network discovery.

`05-active-directory/`

Active Directory administration, authentication, and hands-on labs.

`06-network-security/`

Wireless security, MITM concepts, traffic analysis, and encrypted communication.

`07-offensive-security/`

Reconnaissance, enumeration, Nmap, and controlled security testing.

`08-labs/`

Index of practical cybersecurity exercises.

---

# Tools and Technologies

Tools and technologies appearing throughout my learning notes include:

- Linux
- Windows
- Active Directory
- PowerShell
- Nmap
- Wireshark
- SSH
- OpenVPN
- Bettercap
- Netdiscover
- TryHackMe
- Metasploitable

---

# Learning Method

My approach is:

`Learn the Concept`

↓

`Practice in a Controlled Lab`

↓

`Understand the Output`

↓

`Troubleshoot Problems`

↓

`Document What I Learned`

I focus on understanding why a tool or command is used rather than only memorizing commands.

---

# Security and Ethics

All security testing documented in this repository is performed in controlled or explicitly authorized environments such as:

- TryHackMe
- CTF platforms
- Intentionally vulnerable machines
- Personal lab environments

I do not use these techniques against systems without authorization.

---

# Current Goal

I am currently building a stronger foundation in cybersecurity by combining system administration, networking, Active Directory, and hands-on security labs.

As I continue learning, I will add new notes and practical lab documentation to this repository.
