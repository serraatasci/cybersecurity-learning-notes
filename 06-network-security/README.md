# Network Security

This section contains my notes on network security concepts and controlled lab exercises.

---

## Topics

- Wireless security
- Wireless monitoring
- ARP spoofing concepts
- Man-in-the-Middle (MITM) attacks
- Traffic sniffing
- Bettercap
- MITMf
- HTTPS
- HSTS
- Network traffic protection

---

## Why Network Security Matters

Networking explains how devices communicate.

Network security focuses on how that communication can be:

- Observed
- Protected
- Manipulated
- Monitored
- Investigated

Understanding these concepts helps me see why protocols, encryption, access controls, and secure network configurations are important.

---

## From Networking to Network Security

The previous networking section covered concepts such as:

- IP addresses
- MAC addresses
- ARP
- Ports
- Network discovery

This section builds on those concepts.

For example:

`ARP`

explains how an IP address is mapped to a MAC address.

Network security then examines what can happen when that mapping is manipulated.

Similarly:

`HTTP / HTTPS`

explains web communication.

Network security examines why encryption is needed to protect that traffic.

---

## Man-in-the-Middle Concept

A Man-in-the-Middle attack is a situation where an attacker attempts to position themselves between two communicating systems.

Conceptually:

`Victim`

↓

`Intermediary`

↓

`Router / Server`

If successful, the intermediary may attempt to observe or manipulate the traffic.

The important security lesson is that network communication should not automatically be trusted simply because devices are on the same local network.

---

## Traffic Sniffing

Sniffing means capturing or observing network traffic.

Traffic analysis can be used legitimately for:

- Troubleshooting
- Network monitoring
- Incident investigation
- Security testing

In controlled security labs, traffic sniffing also helps demonstrate why unencrypted protocols can expose sensitive information.

---

## Wireless Security

Wireless networks introduce additional security considerations because communication takes place over radio signals.

The notes in this section include concepts such as:

- Wireless interface modes
- Wireless network monitoring
- Wireless encryption
- Security testing in lab environments

Wireless security is covered separately in:

`wireless-security.md`

---

## HTTPS and Encryption

HTTPS protects communication between a web browser and a web server using encryption.

Conceptually:

`Browser`

↓

`Encrypted HTTPS Traffic`

↓

`Web Server`

Without encryption, network traffic may be easier to inspect.

This is why secure protocols are an important part of network security.

---

## HSTS

HSTS stands for:

`HTTP Strict Transport Security`

It tells a browser that a website should only be accessed using HTTPS.

The basic security idea is:

`Website`

↓

`HTTPS Only`

↓

`Do Not Downgrade to HTTP`

HSTS is covered in more detail in:

`https-and-hsts.md`

---

## Security Tools in My Notes

The tools introduced in this section include:

### Bettercap

A network security framework used for network monitoring and controlled MITM-related lab exercises.

### MITMf

Man-in-the-Middle Framework, used in the course material to demonstrate MITM concepts.

These tools are documented as part of authorized cybersecurity learning and lab environments.

---

## Controlled Lab Use

The concepts in this section can affect other devices and network traffic.

Therefore, all practical work should only be performed on:

- Systems I own
- Networks I control
- TryHackMe environments
- CTF environments
- Other explicitly authorized lab systems

The purpose of these notes is to understand how network attacks work so that I can better understand the corresponding defenses.

---

## Section Structure

This section is organized as:

- `wireless-security.md`
- `arp-spoofing-and-mitm.md`
- `traffic-sniffing.md`
- `https-and-hsts.md`

---

## Learning Perspective

The main security questions I want to understand are:

`Can another device observe this traffic?`

`Is the traffic encrypted?`

`Can local network information be manipulated?`

`How can suspicious network behavior be detected?`

`Which protections prevent these attacks?`

---

## Key Takeaway

Networking explains:

`How communication works`

Network security adds:

`How communication can be attacked or protected`

The main concepts in this section can be simplified as:

`Wireless Security → Protect wireless communication`

`ARP Spoofing / MITM → Manipulation of local communication`

`Sniffing → Observing network traffic`

`HTTPS → Encrypt web traffic`

`HSTS → Enforce HTTPS`
