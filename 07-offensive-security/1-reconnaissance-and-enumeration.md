# Reconnaissance and Enumeration

This page contains my notes on reconnaissance and enumeration in controlled offensive security labs.

The focus of this page is understanding how information about a target is collected in a structured way.

---

## Reconnaissance

Reconnaissance is the process of collecting initial information about a target.

The purpose is to understand the environment before performing deeper analysis.

A simple way to remember:

`Reconnaissance = Find and understand the target`

Questions answered during reconnaissance may include:

- Which IP addresses are active?
- Which systems are reachable?
- Which network services are exposed?
- Which ports appear open?

---

# Enumeration

Enumeration goes deeper than basic discovery.

The goal is to collect more detailed information about discovered services.

A simple way to remember:

`Reconnaissance = What exists?`

`Enumeration = What exactly is running?`

---

# Example

Suppose I discover:

`192.168.1.20`

and then identify:

`Port 21 Open`

This is useful information.

Enumeration goes further:

`Port 21`

↓

`FTP`

↓

`FTP Server Software`

↓

`Version`

This gives a much better understanding of the service.

---

# Reconnaissance vs Enumeration

| Reconnaissance | Enumeration |
|---|---|
| Collects initial target information | Collects detailed service information |
| Finds systems | Analyzes discovered systems |
| Finds ports | Identifies services |
| Builds the initial picture | Builds a deeper technical picture |

A simple memory trick:

`Recon = Find`

`Enumeration = Detail`

---

# Basic Workflow

The basic workflow from my notes can be organized as:

1. Identify the target
2. Check whether the target is reachable
3. Identify open ports
4. Identify services
5. Identify versions
6. Review the findings

Simplified:

`Target`

↓

`Reachability`

↓

`Open Ports`

↓

`Services`

↓

`Versions`

↓

`Analysis`

---

# Target Identification

In a controlled lab, the target is usually provided as an IP address.

Example:

`TARGET_IP`

The important point is to make sure I am scanning the correct authorized system.

---

# Connectivity Check

A basic connectivity check may use:

`ping TARGET_IP`

This can help determine whether the target appears reachable.

However:

`No ping response ≠ Target is offline`

because ICMP may be blocked or filtered.

---

# Port Discovery

The next step is identifying which ports are open.

An open port may indicate that a network service is listening.

Example:

`22/tcp open`

This suggests that a service is accepting connections on port 22.

---

# Service Identification

The next question is:

`Which service is using the open port?`

For example:

`22/tcp open ssh`

This indicates that SSH appears to be running.

Other examples from my notes include:

- FTP
- Telnet
- HTTP
- SSH

---

# Version Identification

After identifying the service, the next useful step is determining the software version.

Example:

`FTP`

↓

`FTP Software`

↓

`Version`

This information can help reveal whether the service is outdated.

---

# Why Version Information Matters

A service name alone does not provide the full security picture.

For example:

`SSH`

may be present on two systems.

But:

`System A`

and:

`System B`

may run different SSH versions.

The exact version can be relevant when checking whether software is old or has known security issues.

---

# Nmap in the Workflow

Nmap is one of the main tools used in my notes for reconnaissance and enumeration.

It can help identify:

- Open ports
- Services
- Service versions
- Operating system information

This makes it useful across both reconnaissance and enumeration.

---

# Netdiscover in the Workflow

Netdiscover is useful for identifying devices on a local network.

Its role is more focused on:

`IP + MAC discovery`

A simple distinction is:

`Netdiscover = Find devices`

`Nmap = Analyze services`

---

# Organizing Findings

A useful habit is to organize findings instead of only reading terminal output.

For example:

| Target | Port | Service | Version |
|---|---|---|---|
| `TARGET_IP` | 21 | FTP | Identified during scan |
| `TARGET_IP` | 22 | SSH | Identified during scan |
| `TARGET_IP` | 80 | HTTP | Identified during scan |

This makes later analysis easier.

---

# Save Scan Results

My notes also include saving scan results.

This is useful because I can:

- Review findings later
- Avoid repeating the same scan
- Compare results
- Document lab progress

A useful workflow is:

`Run Scan`

↓

`Save Output`

↓

`Review`

↓

`Document`

---

# Enumeration Is Not Exploitation

An important distinction is:

`Enumeration`

does not automatically mean:

`Exploitation`

Enumeration is focused on gathering technical information.

The purpose is to understand the exposed services before deciding what the next security analysis step should be.

---

# Service Questions

For each service, useful questions include:

- Which port is open?
- Which service is running?
- Which version is running?
- Is authentication required?
- Is anonymous access allowed?
- Is the software outdated?
- Is the configuration secure?

These questions create a structured assessment process.

---

# Example: FTP

If I discover:

`21/tcp open ftp`

I can then ask:

- Is anonymous login enabled?
- Which FTP software is running?
- Which version is running?
- Which files are exposed?
- Is authentication required?

This is enumeration.

---

# Example: SSH

If I discover:

`22/tcp open ssh`

I can then ask:

- Which SSH version is running?
- Which authentication methods are enabled?
- Is the service exposed intentionally?
- Is the software up to date?

---

# Example: HTTP

If I discover:

`80/tcp open http`

I can then ask:

- Which web server is running?
- Which version is running?
- What application is hosted?
- Is HTTPS also available?

---

# Reconnaissance Mindset

Instead of randomly running tools, I try to follow a consistent process:

`What is the target?`

↓

`What is reachable?`

↓

`What is exposed?`

↓

`What services are running?`

↓

`What versions are running?`

↓

`What should I investigate next?`

---

# Controlled Lab Use

All reconnaissance and enumeration in these notes are intended for:

- TryHackMe labs
- CTF environments
- Metasploitable
- Personal test systems
- Explicitly authorized environments

A core rule is:

`Only scan systems where I have permission.`

---

# Quick Reference

| Term | Meaning |
|---|---|
| Reconnaissance | Initial information gathering |
| Enumeration | Detailed information gathering |
| Target | Authorized system being analyzed |
| Open Port | Port accepting connections |
| Service | Network functionality exposed on a port |
| Version Detection | Identifying software version |
| Nmap | Network and service discovery tool |
| Netdiscover | Local device discovery tool |

---

## Key Takeaway

The easiest way to remember the workflow is:

`Reconnaissance → Enumeration → Analysis`

And the difference is:

`Reconnaissance = Find what exists`

`Enumeration = Learn details about what exists`

A structured workflow is:

`Target → Ports → Services → Versions → Findings`
