# HTTPS and HSTS

This page contains my notes on HTTPS, SSL/TLS, HSTS, and why encrypted web communication is important in network security.

---

## What Is HTTPS?

HTTPS stands for:

`Hypertext Transfer Protocol Secure`

It is the secure version of HTTP.

HTTPS protects communication between:

`Web Browser`

and:

`Web Server`

by using encryption.

A simple way to remember:

`HTTP = Web communication`

`HTTPS = Encrypted web communication`

---

# HTTPS Communication

Without encryption, web traffic may be easier to inspect.

With HTTPS:

`Browser`

↓

`Encrypted Traffic`

↓

`Web Server`

This helps protect the data exchanged between the browser and server.

---

# SSL / TLS

My notes describe HTTPS as using:

`SSL / TLS`

for encrypted communication.

The important concept is:

`Browser and Server`

↓

`Encrypted Session`

↓

`Protected Web Traffic`

The goal is to prevent other systems on the network from simply reading the web traffic as plaintext.

---

# Why Encryption Matters

Web traffic may contain sensitive information such as:

- Login credentials
- Session information
- Personal information
- Application data

If this information is transmitted without encryption, someone able to observe the traffic may potentially read it.

HTTPS reduces this risk by encrypting the communication.

---

# HTTP vs HTTPS

| HTTP | HTTPS |
|---|---|
| Web communication | Secure web communication |
| Traffic is not protected by HTTPS encryption | Traffic is encrypted |
| More exposed to traffic observation | Protects application content |
| Common port 80 | Common port 443 |

The easiest way to remember:

`HTTPS = HTTP + Encryption`

---

# HTTPS and MITM

In a Man-in-the-Middle scenario, an intermediary may be positioned between:

`Victim`

and:

`Web Server`

Conceptually:

`Victim`

↓

`Intermediary`

↓

`Server`

If the traffic is properly protected with HTTPS, simply being in the middle does not automatically reveal the readable web content.

This is one of the main reasons HTTPS is important.

---

# HTTPS Downgrade Concept

My notes mention the idea of attempting to change:

`HTTPS`

into:

`HTTP`

during a MITM-related demonstration.

The security idea behind this is that HTTP traffic does not provide the same encryption protection as HTTPS.

Conceptually:

`Secure HTTPS`

↓

`Downgrade Attempt`

↓

`Insecure HTTP`

If successful, this would reduce the protection provided by encryption.

This is one reason mechanisms such as HSTS are important.

---

# What Is HSTS?

HSTS stands for:

`HTTP Strict Transport Security`

HSTS allows a website to tell the browser:

`Only communicate with me using HTTPS.`

A simple way to remember:

`HSTS = HTTPS Only`

---

# Basic HSTS Logic

Without strict HTTPS enforcement, a browser might attempt an HTTP connection before switching to HTTPS.

HSTS tells the browser not to use the insecure HTTP version.

Simplified:

`User requests website`

↓

`Browser knows HSTS policy`

↓

`Use HTTPS`

↓

`Do not use HTTP`

---

# Why HSTS Matters

HSTS helps protect against situations where communication could otherwise be downgraded from:

`HTTPS`

to:

`HTTP`

The main security principle is:

`Do not allow insecure HTTP when HTTPS should be used.`

---

# HSTS and MITM

In a MITM scenario, an attacker may attempt to interfere with the connection between the browser and web server.

HSTS helps reduce downgrade opportunities by telling the browser to require HTTPS.

Conceptually:

`MITM tries to force HTTP`

↓

`Browser has HSTS policy`

↓

`Browser requires HTTPS`

↓

`HTTP downgrade rejected`

---

# HTTPS Does Not Mean the Network Is Trusted

HTTPS protects the communication even when the network itself may not be trustworthy.

For example:

`Public Wi-Fi`

may contain unknown or untrusted devices.

HTTPS helps protect web traffic from being easily read by other systems on the same network.

A useful security mindset is:

`Untrusted Network`

+

`Encrypted Protocol`

=

`Safer Communication`

---

# VPN and HTTPS

My notes also mention VPN as a possible protection when using an untrusted network.

VPN and HTTPS protect communication in different ways.

`HTTPS`

→ Protects communication between browser and web server

`VPN`

→ Creates a protected virtual network connection

They are separate security mechanisms and can be used together.

---

# Detecting Suspicious Local Network Behavior

The notes also mention that unexpected IP-to-MAC relationships involving the router may indicate suspicious activity.

For example:

`Gateway IP`

should normally correspond to:

`Router MAC`

If the expected mapping changes unexpectedly, it may be worth investigating for MITM-related behavior.

This connects HTTPS/HSTS protection with the earlier ARP spoofing topic.

---

# HTTPS and Traffic Sniffing

When traffic is captured:

`HTTP Traffic`

may expose readable application information.

While:

`HTTPS Traffic`

is designed to keep the application content encrypted.

So:

`Capture ≠ Automatically Read`

when HTTPS encryption is working correctly.

---

# Security Layers

HTTPS and HSTS work as part of multiple security layers.

A simplified model is:

`HTTPS`

→ Encrypt web traffic

`HSTS`

→ Require HTTPS

`VPN`

→ Protect the network connection

`ARP Monitoring`

→ Detect suspicious local network mappings

This demonstrates the idea of:

`Defense in Depth`

---

# Controlled Lab Perspective

The HTTPS downgrade concept in these notes comes from controlled cybersecurity training.

The purpose is to understand:

- Why HTTP is risky
- Why HTTPS matters
- Why downgrade protection matters
- How MITM attacks interact with encrypted traffic

---

# Quick Reference

| Term | Meaning |
|---|---|
| HTTP | Hypertext Transfer Protocol |
| HTTPS | Secure encrypted version of HTTP |
| SSL/TLS | Encryption technologies used with HTTPS |
| HSTS | HTTP Strict Transport Security |
| MITM | Man-in-the-Middle |
| Downgrade | Attempt to replace a secure connection with a weaker one |
| VPN | Virtual Private Network |
| Port 80 | Common HTTP port |
| Port 443 | Common HTTPS port |

---

## Key Takeaway

The easiest way to remember the concepts is:

`HTTP = Web traffic`

`HTTPS = Encrypted web traffic`

`HSTS = HTTPS only`

and:

`MITM Position ≠ Automatic Decryption`

The main defensive idea is:

`Encrypt communication and prevent downgrade to insecure protocols.`
