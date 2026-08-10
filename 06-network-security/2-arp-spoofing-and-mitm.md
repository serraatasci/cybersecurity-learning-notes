# ARP Spoofing and Man-in-the-Middle

This page contains my notes on ARP spoofing and Man-in-the-Middle (MITM) concepts from controlled cybersecurity labs.

The focus of this page is understanding how local network trust can be manipulated and why secure network protections are important.

---

## What Is ARP Spoofing?

ARP normally maps:

`IP Address → MAC Address`

Inside a local network, devices use ARP information to determine which MAC address belongs to a specific IP address.

ARP spoofing attempts to manipulate this relationship.

A simplified idea is:

`Victim believes attacker MAC = Router IP`

and:

`Router believes attacker MAC = Victim IP`

This can cause traffic to pass through the intermediary system.

---

# Normal Communication

Without manipulation, communication may look like:

`Victim`

↓

`Router`

↓

`Internet / Remote Server`

The victim uses the router's actual MAC address for local delivery.

---

# Manipulated Communication

In an ARP spoofing scenario, the traffic path may become:

`Victim`

↓

`Attacker / Intermediary`

↓

`Router`

↓

`Internet`

The attacker attempts to position themselves between the victim and router.

This is one example of a:

`Man-in-the-Middle`

situation.

---

# Man-in-the-Middle — MITM

MITM stands for:

`Man-in-the-Middle`

A MITM situation occurs when an intermediary positions itself between two communicating systems.

Conceptually:

`Victim`

↓

`Intermediary`

↓

`Router / Server`

If the intermediary can receive the traffic, it may attempt to:

- Observe traffic
- Analyze communication
- Forward packets
- Manipulate certain traffic

The exact impact depends heavily on whether the communication is encrypted.

---

# ARP Trust Problem

ARP relies on local network information about which MAC address belongs to which IP address.

If incorrect information is accepted, the device may store a false mapping.

For example, the victim may incorrectly learn:

`Gateway IP → Attacker MAC`

instead of:

`Gateway IP → Real Router MAC`

This is the basic idea behind ARP spoofing.

---

# ARP Table Perspective

Normally, the ARP table might contain:

| IP Address | MAC Address |
|---|---|
| Gateway IP | Router MAC |
| Victim IP | Victim MAC |

After ARP manipulation, a suspicious mapping could appear conceptually as:

| IP Address | MAC Address |
|---|---|
| Gateway IP | Unexpected MAC |

If the known gateway suddenly maps to an unfamiliar MAC address, this can be worth investigating.

---

# Why the Gateway Is Important

The default gateway is normally the local router used to reach other networks.

For traffic going to the Internet:

`Victim`

↓

`Default Gateway`

↓

`External Network`

Because much of the victim's external traffic goes through the gateway, manipulating the gateway's ARP mapping can affect a large amount of communication.

---

# Traffic Forwarding

For a MITM position to remain useful, intercepted traffic generally needs to continue toward the real destination.

Conceptually:

`Victim Traffic`

↓

`Intermediary`

↓

`Forwarded to Router`

If traffic is not forwarded, the victim may simply lose network connectivity.

This is why MITM scenarios often involve both:

- Interception
- Forwarding

---

# Bettercap

My notes include:

`Bettercap`

Bettercap is a network security framework used in controlled lab environments for activities such as:

- Network reconnaissance
- Network monitoring
- ARP-related lab exercises
- MITM demonstrations

In my learning, Bettercap helped connect the theoretical ARP concept with practical local network behavior.

---

# Bettercap Network Discovery

The notes use Bettercap functionality such as:

`net.probe`

and:

`net.recon`

These relate to discovering or observing devices on the local network.

The general purpose is:

`Local Network`

↓

`Identify Devices`

↓

`Understand IP / MAC relationships`

This information is useful before analyzing local network communication.

---

# ARP Spoofing Module Concept

The notes also reference:

`arp.spoof`

The important concept is that the target and network gateway must be identified correctly in a controlled lab before an ARP spoofing demonstration can take place.

Rather than focusing on memorizing commands, the main idea is:

`Identify Victim`

+

`Identify Gateway`

↓

`Manipulate ARP relationships`

↓

`Traffic may pass through intermediary`

---

# MITMf

My notes also include:

`MITMf`

which stands for:

`Man-in-the-Middle Framework`

It was used in the course material to demonstrate MITM concepts.

The tool represents the same general security idea:

`Position between communicating devices`

↓

`Observe how traffic behaves`

↓

`Understand the importance of network protections`

---

# What Happens to Traffic?

If the intermediary successfully positions itself between the victim and router, it may be able to observe some network metadata and traffic.

However, the amount of readable information depends on the protocols being used.

For example:

`Unencrypted Traffic`

may expose more information.

While:

`Encrypted Traffic`

is designed to prevent the intermediary from simply reading the application content.

This is why HTTPS and other encrypted protocols are important.

---

# ARP Spoofing Does Not Automatically Break HTTPS

An important distinction is:

`MITM Position ≠ Automatic Decryption`

Being between two systems does not automatically reveal encrypted HTTPS content.

Encryption still protects the communication.

This leads directly to the security topics covered in:

`https-and-hsts.md`

---

# Why Plaintext Protocols Are Riskier

If a protocol sends information without encryption, an intermediary may be able to observe more of the traffic.

This is one reason older or insecure protocols are risky.

Examples previously covered include:

`Telnet`

and basic:

`HTTP`

when compared with encrypted alternatives such as:

`SSH`

and:

`HTTPS`

---

# Detecting Suspicious ARP Behavior

Possible warning signs can include:

- Unexpected MAC address changes
- Gateway IP mapping to an unfamiliar MAC address
- Duplicate or unusual ARP mappings
- Sudden network instability
- Unexpected intermediary behavior

ARP information can therefore be useful during network troubleshooting and security analysis.

---

# Defensive Perspective

The security lesson is not only how ARP manipulation works.

The more important question is:

`How can local network communication be protected?`

Useful defensive ideas include:

- Using encrypted protocols
- Monitoring unusual ARP changes
- Segmenting networks
- Avoiding unnecessary trust on local networks
- Monitoring endpoints and network traffic

---

# ARP Spoofing vs MITM

These terms are related but not identical.

`ARP Spoofing`

→ Technique that manipulates local IP-to-MAC mappings

`MITM`

→ Broader attack position where an intermediary sits between communicating systems

ARP spoofing can be one way to achieve a MITM position on a local network.

Simplified:

`ARP Spoofing`

↓

`MITM Position`

↓

`Traffic Observation / Manipulation Possibility`

---

# Networking Concepts Used Here

This topic depends heavily on earlier networking fundamentals:

`IP Address`

↓

`ARP`

↓

`MAC Address`

and:

`Victim`

↓

`Default Gateway`

↓

`Internet`

Understanding ARP and default gateways makes the MITM concept much easier to understand.

---

# Controlled Lab Use

ARP spoofing can disrupt real network traffic.

The practical concepts in this section were learned for controlled cybersecurity practice.

Testing should only be performed in:

- Networks I own
- Authorized lab networks
- TryHackMe environments
- CTF environments
- Other explicitly permitted systems

---

# Quick Reference

| Term | Meaning |
|---|---|
| ARP | Maps IP addresses to MAC addresses |
| ARP Spoofing | Manipulating IP-to-MAC mappings |
| MITM | Man-in-the-Middle |
| Default Gateway | Router used to reach other networks |
| Bettercap | Network security and MITM lab framework |
| MITMf | Man-in-the-Middle Framework |
| `net.probe` | Bettercap network discovery concept |
| `net.recon` | Bettercap network reconnaissance concept |
| `arp.spoof` | Bettercap ARP spoofing functionality |
| Traffic Forwarding | Passing intercepted traffic toward its destination |

---

## Key Takeaway

The easiest way to understand the concept is:

`Normal`

`Victim → Router`

After ARP manipulation:

`Victim → Intermediary → Router`

The underlying problem is:

`Incorrect ARP information can change where local traffic is sent.`

The main defensive lesson is:

`Do not rely only on local network trust.`

Encrypted protocols, network monitoring, and secure configurations are important because a device on the same local network may not always be trustworthy.
