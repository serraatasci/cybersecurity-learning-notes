# Nmap Service Analysis

This page contains my notes on using Nmap to identify open ports, services, service versions, and basic target information in controlled cybersecurity labs.

---

## What Is Nmap?

Nmap stands for:

`Network Mapper`

Nmap is used to discover and analyze systems and services on a network.

In my learning, Nmap is mainly used to identify:

- Open ports
- Running services
- Service versions
- Operating system information
- Additional service details

---

# Basic Nmap Scan

The most basic idea is:

`nmap TARGET_IP`

This scans the target and reports information about reachable ports and services.

---

# Command Used in My Notes

One of the commands used in my course notes is:

`nmap -v -sS -A -T4 TARGET_IP`

This combines several Nmap options.

The options are:

- `-v`
- `-sS`
- `-A`
- `-T4`

---

# `-v` — Verbose

`-v`

means:

`Verbose`

Verbose output displays more information while Nmap is running.

A simple way to remember:

`-v = Show more details`

---

# `-sS` — TCP SYN Scan

`-sS`

performs a:

`TCP SYN Scan`

It is also commonly called:

`Half-Open Scan`

---

## TCP Connection Concept

A normal TCP connection begins with:

`SYN`

↓

`SYN/ACK`

↓

`ACK`

During a SYN scan, Nmap sends a SYN packet.

If it receives:

`SYN/ACK`

the port appears to be open.

The full TCP connection does not need to be completed.

Simplified:

`Send SYN`

↓

`Receive SYN/ACK`

↓

`Port appears open`

---

# `-A` — Aggressive Scan

The notes use:

`-A`

for broader information gathering.

The course associates this option with capabilities such as:

- Service/version detection
- Operating system detection
- Script scanning
- Traceroute

A simple way to remember:

`-A = Collect more information`

---

# `-T4` — Timing

`-T4`

controls the scan timing profile.

In my lab notes, it is used to make scanning faster in appropriate controlled environments.

A simple way to remember:

`-T4 = Faster scan timing`

---

# Reading Nmap Output

Nmap output often contains columns such as:

`PORT`

`STATE`

`SERVICE`

Example:

| Port | State | Service |
|---|---|---|
| 21/tcp | open | ftp |
| 22/tcp | open | ssh |
| 80/tcp | open | http |

---

# Port

The port number identifies a network service endpoint.

Examples:

`21`

`22`

`80`

The port itself gives an initial clue about what may be running.

---

# State

Nmap reports a state for each scanned port.

A common state is:

`open`

This means a service appears to be accepting connections on that port.

---

# Service

The service field gives Nmap's estimate of what protocol or service is running.

Examples:

`21 → FTP`

`22 → SSH`

`80 → HTTP`

However, a service can be configured on a non-standard port.

Therefore, the port number alone is not always enough.

---

# Service Detection

Service detection attempts to determine what is actually running behind the port.

For example:

`Port 21`

↓

`FTP`

This gives more useful information than only knowing the port number.

---

# Version Detection

Version detection goes one step further.

Example:

`Port 21`

↓

`FTP`

↓

`FTP Server Software`

↓

`Version`

The exact software version can be important during a security assessment.

---

# Why Versions Matter

Different versions of the same software may have different security properties.

An older service version may have known vulnerabilities.

The general workflow is:

`Find Service`

↓

`Identify Version`

↓

`Review Security Relevance`

This is one reason software updates and patch management are important.

---

# Operating System Detection

The notes also include operating system detection.

Nmap can attempt to identify whether the target is running an operating system such as:

- Linux
- Windows

This helps build a more complete profile of the target.

---

# Script Scanning

The course notes also mention Nmap script scanning.

The basic idea is:

`Open Port`

↓

`Service`

↓

`Run additional checks`

↓

`Collect more information`

At my current learning level, the most important point is that Nmap can gather more than only port numbers.

---

# Example Service Analysis

Suppose Nmap returns:

`21/tcp open ftp`

The analysis should not stop there.

Useful questions include:

- Which FTP server software is running?
- Which version is running?
- Is authentication required?
- Is anonymous login enabled?
- Is the software outdated?

This is where basic scanning turns into enumeration.

---

# Example SSH Analysis

Suppose the result includes:

`22/tcp open ssh`

Useful follow-up questions include:

- Which SSH implementation is running?
- Which version is running?
- Is the service intentionally exposed?
- Is the service current and patched?

---

# Example HTTP Analysis

Suppose the result includes:

`80/tcp open http`

Useful questions include:

- Which web server is running?
- Which version is running?
- Is HTTPS also available?
- What application is hosted?

---

# Saving Nmap Output

My notes also include saving scan results to a file.

This is useful for:

- Reviewing results later
- Documenting lab work
- Comparing scans
- Avoiding unnecessary repeated scans

A useful workflow is:

`Run Scan`

↓

`Save Output`

↓

`Review`

↓

`Document`

---

# Example Output File Concept

A scan can be saved and reviewed later.

This is especially useful in larger labs where multiple systems and services are being analyzed.

The important habit is:

`Do not rely only on terminal history`

Document findings in a structured way.

---

# Service Analysis Table

A simple way to organize findings is:

| Target | Port | Service | Version | Notes |
|---|---|---|---|---|
| `TARGET_IP` | 21 | FTP | Identified in scan | Review authentication |
| `TARGET_IP` | 22 | SSH | Identified in scan | Review version |
| `TARGET_IP` | 80 | HTTP | Identified in scan | Review web service |

This makes the scan easier to interpret.

---

# Nmap Is Not the Final Step

Nmap provides information.

It does not automatically determine whether a system is vulnerable.

A scan result such as:

`Port 21 open`

does not automatically mean:

`The system is vulnerable`

Further analysis is required.

The correct mindset is:

`Nmap Finding`

↓

`Understand Service`

↓

`Understand Version`

↓

`Evaluate Security`

---

# Scan Results and Vulnerability Assessment

Nmap results can support vulnerability assessment.

For example:

`Service Version`

↓

`Known Security History`

↓

`Potential Risk`

But version information should be interpreted carefully.

A service may be:

- Patched
- Backported
- Configured differently
- Protected by additional controls

Therefore, the scan result is evidence for investigation, not automatic proof of exploitation.

---

# Nmap in My Learning Workflow

The workflow I use is:

1. Identify the target
2. Run Nmap
3. Review open ports
4. Identify services
5. Identify versions
6. Note operating system information
7. Document findings
8. Decide what should be investigated further

Simplified:

`Target`

↓

`Nmap`

↓

`Ports`

↓

`Services`

↓

`Versions`

↓

`Analysis`

---

# Controlled Lab Use

Nmap can generate network traffic that may be detected or blocked.

All scanning in these notes is intended for:

- TryHackMe labs
- CTF environments
- Metasploitable
- Personal test machines
- Other explicitly authorized systems

A core rule is:

`Only scan systems where I have permission.`

---

# Quick Reference

| Option / Term | Meaning |
|---|---|
| Nmap | Network Mapper |
| `-v` | Verbose output |
| `-sS` | TCP SYN scan |
| `-A` | Broader information gathering |
| `-T4` | Faster timing profile |
| Open Port | Port accepting connections |
| Service Detection | Identify the service |
| Version Detection | Identify software version |
| OS Detection | Estimate operating system |
| Script Scanning | Gather additional service information |

---

## Key Takeaway

The main Nmap workflow is:

`Scan → Ports → Services → Versions → Analysis`

The important lesson is:

`An open port is only the beginning.`

The real value comes from understanding:

`What service is running?`

`Which version is running?`

`Why is it exposed?`

`Does it require further security analysis?`
