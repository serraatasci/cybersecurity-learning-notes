# Hands-On Labs

This section contains summaries of my hands-on cybersecurity practice.

Instead of duplicating the full technical notes, this page acts as an index for practical lab work documented across the repository.

---

## Active Directory Administration Lab

### Topics Practiced

- Organizational Unit management
- Active Directory delegation
- Principle of Least Privilege
- Password reset permissions
- PowerShell administration
- Password policy troubleshooting
- RDP validation
- Domain user authentication

### Lab Summary

In this lab, I reviewed an existing Active Directory environment and updated the OU structure to match the organization.

I then delegated password reset permissions for the Sales OU to an IT Support user without giving full Domain Administrator privileges.

The delegated permission was tested using the support user's own account.

During the process, I encountered and troubleshot:

- Accidental deletion protection
- Access denied errors
- Domain password complexity requirements
- RDP / NLA behavior
- Password change at next logon settings

The final result was validated by successfully authenticating with the updated user account.

Full write-up:

`../05-active-directory/hands-on-administration-lab.md`

---

## Windows Administration Practice

### Topics Practiced

- Windows user management
- Local users and groups
- UAC
- Event Viewer
- Task Scheduler
- Services
- Resource Monitor
- Registry
- Windows Security tools

Related notes:

`../03-windows/`

---

## Linux Practice

### Topics Practiced

- Linux command line
- File system navigation
- File permissions
- Search and text processing
- SSH
- SCP
- Package management
- Cron
- Log analysis

Related notes:

`../02-linux/`

---

## Network Discovery Practice

### Topics Practiced

- Basic connectivity testing
- IP and MAC addressing
- ARP
- Network discovery
- Nmap
- Port scanning
- Service detection
- Version identification

Related notes:

`../04-networking/`

and:

`../07-offensive-security/`

---

## Network Security Labs

### Topics Practiced

- Wireless monitoring concepts
- Monitor Mode
- Traffic sniffing
- ARP spoofing concepts
- Man-in-the-Middle concepts
- HTTPS
- HSTS
- Encrypted vs plaintext traffic

Related notes:

`../06-network-security/`

---

## Lab Environment

My practical work is performed in controlled or explicitly authorized environments such as:

- TryHackMe
- CTF environments
- Intentionally vulnerable machines
- Personal lab systems

I use these environments to understand security concepts without targeting real production systems.

---

## My Lab Documentation Approach

For each lab, I try to focus on:

`Objective`

↓

`Environment`

↓

`Tools / Commands`

↓

`Results`

↓

`Errors`

↓

`Troubleshooting`

↓

`Security Concept Learned`

This helps me understand why each step is performed instead of only memorizing commands.

---

## Key Takeaway

The goal of this section is not to collect flags or screenshots.

The goal is to demonstrate:

- Practical understanding
- Troubleshooting
- Security reasoning
- Hands-on experience

My theoretical notes explain the concepts, while this section highlights where I applied them in practice.
