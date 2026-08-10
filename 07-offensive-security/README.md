# Offensive Security

This section contains my introductory offensive security notes and hands-on practice from controlled cybersecurity labs.

---

## Topics

- Penetration testing fundamentals
- Reconnaissance
- Enumeration
- Nmap scanning
- Open port analysis
- Service detection
- Version detection
- Operating system identification
- CTF environments
- Metasploitable
- Basic service assessment

---

## What Is Offensive Security?

Offensive Security focuses on identifying and understanding security weaknesses by approaching systems from an attacker's perspective.

The purpose is not simply to attack systems.

The goal is to understand:

- What is exposed
- Which services are available
- Which weaknesses may exist
- How those weaknesses can be identified
- How organizations can improve their defenses

---

## Penetration Testing

Penetration testing is an authorized security assessment performed to identify weaknesses in systems, networks, or applications.

A simplified process can look like:

`Reconnaissance`

↓

`Enumeration`

↓

`Identify Services`

↓

`Analyze Potential Weaknesses`

↓

`Validate Findings`

↓

`Report and Remediate`

---

## Authorization

Offensive security activities must only be performed on systems where testing is explicitly allowed.

Examples include:

- TryHackMe labs
- CTF environments
- Metasploitable
- Personal lab machines
- Explicitly authorized systems

A useful rule is:

`No Authorization = No Testing`

---

# Reconnaissance

Reconnaissance is the process of collecting information about a target environment.

The goal is to answer questions such as:

- Which systems exist?
- Which IP addresses are active?
- Which ports are open?
- Which services are running?

In my learning, tools such as Nmap are used during this stage.

---

# Enumeration

Enumeration goes deeper than simply discovering that a system exists.

The goal is to gather detailed information about exposed services.

For example:

`Port 21 Open`

is useful information.

But:

`Port 21 → FTP → Specific Server Version`

provides much more useful context.

A simple way to remember:

`Reconnaissance = Find the target`

`Enumeration = Learn more about the target`

---

# Nmap

Nmap is one of the main tools covered in my offensive security notes.

Nmap stands for:

`Network Mapper`

It can help identify:

- Open ports
- Network services
- Service versions
- Operating system information
- Additional service details

---

# Example Nmap Scan

A command used in my course notes is:

`nmap -v -sS -A -T4 TARGET_IP`

The main options are:

`-v`

→ Verbose output

`-sS`

→ TCP SYN scan

`-A`

→ Enables broader information gathering such as version detection, operating system detection, script scanning, and traceroute

`-T4`

→ Uses a faster timing profile for appropriate lab networks

---

# TCP SYN Scan

The `-sS` option performs a TCP SYN scan.

A normal TCP connection begins with:

`SYN`

↓

`SYN/ACK`

↓

`ACK`

During a SYN scan, Nmap can use the response to determine whether a port appears open without completing the full connection.

Simplified:

`Send SYN`

↓

`Receive SYN/ACK`

↓

`Port appears open`

---

# Service Detection

Finding an open port is only the beginning.

The next question is:

`Which service is using this port?`

Example:

`21/tcp open ftp`

This indicates that an FTP service appears to be available.

Other examples may include:

`22 → SSH`

`23 → Telnet`

`80 → HTTP`

---

# Version Detection

The exact software version can provide additional information.

Example:

`FTP`

↓

`FTP Server Software`

↓

`Version`

An outdated service version may have known security weaknesses.

This is why version identification is an important part of enumeration.

---

# Operating System Detection

Nmap can also attempt to identify the target operating system.

Examples may include:

- Linux
- Windows

Knowing the operating system helps build a more complete understanding of the target environment.

---

# Script Scanning

Nmap can use scripts to gather additional information about exposed services.

In my current learning, the main idea is:

`Port`

↓

`Service`

↓

`Additional Service Information`

This can help determine which areas deserve further investigation.

---

# Saving Scan Results

My notes also include saving Nmap output to a file.

This is useful because scan results can be reviewed later instead of repeating the scan.

In a real security assessment, documenting findings is important.

A useful workflow is:

`Run Scan`

↓

`Save Results`

↓

`Review`

↓

`Document Findings`

---

# CTF — Capture the Flag

CTF stands for:

`Capture the Flag`

CTFs are cybersecurity learning environments where participants solve security challenges.

The goal may involve finding a:

`Flag`

which proves that a task or challenge has been completed.

CTFs provide a safe environment for practicing cybersecurity skills.

---

# Why CTFs Are Useful

CTFs allow me to practice concepts such as:

- Networking
- Linux
- Windows
- Enumeration
- Service analysis
- Web security
- Privilege concepts

without targeting real production systems.

---

# Metasploitable

My notes also introduce:

`Metasploitable`

Metasploitable is an intentionally vulnerable system designed for security training.

It provides a controlled environment where known weaknesses can be studied safely.

A simple way to think about it is:

`Intentionally Vulnerable Machine`

↓

`Security Practice`

↓

`Learn How Weaknesses Are Identified`

---

# Service Assessment Example

Suppose Nmap returns:

`21/tcp open ftp`

The next questions may include:

- Does the service require authentication?
- Is anonymous access enabled?
- Which FTP software is running?
- Which version is running?
- Is the configuration secure?

This demonstrates why enumeration is more than simply collecting port numbers.

---

# Anonymous FTP

My notes mention:

`Anonymous Login`

Some FTP services may allow a user to connect using an anonymous account.

From a security perspective, the important question is:

`What information or files are exposed without normal authentication?`

Anonymous access is not automatically a vulnerability, but incorrect permissions can expose sensitive information.

---

# Outdated Services

An important lesson from the course is that old software versions may contain known vulnerabilities.

The workflow is:

`Discover Service`

↓

`Identify Version`

↓

`Research Security History`

↓

`Determine Risk`

This is one reason patching and software updates are important defensive controls.

---

# Offensive and Defensive Security

Offensive security and defensive security support each other.

Offensive perspective:

`How could this weakness be identified or abused?`

Defensive perspective:

`How can this weakness be fixed or detected?`

Examples:

`Outdated Service`

→ Offensive: identify exposed version

→ Defensive: patch or upgrade

`Anonymous Access`

→ Offensive: identify exposed files

→ Defensive: restrict permissions

---

# My Learning Workflow

The workflow I am building through my labs is:

1. Understand the target environment
2. Discover exposed systems
3. Identify open ports
4. Identify services
5. Identify service versions
6. Understand the security implications
7. Document findings

This gives me a structured approach instead of randomly running tools.

---

# Section Structure

This section will contain:

- `reconnaissance-and-enumeration.md`
- `nmap-service-analysis.md`
- `ctf-and-lab-environments.md`

The network fundamentals behind Nmap are documented separately under:

`04-networking`

---

# Quick Reference

| Term | Meaning |
|---|---|
| Offensive Security | Security testing from an attacker's perspective |
| Penetration Testing | Authorized testing for security weaknesses |
| Reconnaissance | Collect initial information about a target |
| Enumeration | Gather detailed information about services |
| Nmap | Network Mapper |
| Open Port | Network port accepting connections |
| Service Detection | Identify the service behind a port |
| Version Detection | Identify software version |
| CTF | Capture the Flag |
| Metasploitable | Intentionally vulnerable training system |

---

## Key Takeaway

The main workflow is:

`Discover → Enumerate → Analyze → Document`

And the most important rule is:

`Only test systems where I have authorization.`

The purpose of offensive security is to understand weaknesses so that they can be identified, communicated, and fixed.
