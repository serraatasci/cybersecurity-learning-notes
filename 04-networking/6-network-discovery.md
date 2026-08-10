# Network Discovery

This page contains my notes on basic network discovery and service enumeration using tools such as Netdiscover and Nmap.

All examples in this section are intended for controlled or authorized lab environments.

---

## What Is Network Discovery?

Network discovery is the process of identifying devices and services that exist on a network.

A basic discovery process may answer questions such as:

- Which devices are active?
- Which IP addresses are in use?
- Which MAC addresses belong to those devices?
- Which ports are open?
- Which services are running?
- Which software versions are exposed?

A simple workflow is:

`Discover Devices`

↓

`Identify IP Addresses`

↓

`Identify Open Ports`

↓

`Identify Services`

↓

`Identify Versions`

---

# Netdiscover

Netdiscover is used in my notes to discover devices on a local network.

Its main purpose is to identify relationships between:

`IP Address`

and:

`MAC Address`

A simple way to remember:

`Netdiscover = Find devices on the local network`

---

# Network Interface

Netdiscover can be run using a specific network interface.

The notes use the:

`-i`

option for the interface.

Conceptually:

`-i = Interface`

For example, the interface might be:

`eth0`

or a wireless interface depending on the lab environment.

---

# IP Range

The notes use:

`-r`

to define the IP range that should be scanned.

A network range may look like:

`192.168.1.0/24`

The `/24` notation represents a subnet containing a range of addresses.

In the context of the notes, this allows discovery across devices in that IP range.

---

# Number of Requests

The notes also mention:

`-c`

for controlling the number of discovery requests.

For example:

`-c 10`

means the tool will use the configured request count during discovery.

---

# Netdiscover Result

The goal is to identify information such as:

| IP Address | MAC Address |
|---|---|
| `192.168.1.1` | `AA:BB:CC:DD:EE:FF` |
| `192.168.1.20` | `11:22:33:44:55:66` |

This helps create a basic map of devices on the local network.

---

# Nmap

Nmap stands for:

`Network Mapper`

Nmap is a more comprehensive network discovery and scanning tool.

My notes highlight an important difference:

`Netdiscover`

→ Mainly useful for discovering IP and MAC relationships

`Nmap`

→ Can also identify open ports and services

This makes Nmap useful for deeper network reconnaissance.

---

# Basic Nmap Concept

A simple Nmap scan targets an IP address.

Conceptually:

`Nmap`

↓

`Target IP`

↓

`Check Network Services`

↓

`Display Open Ports`

Example structure:

`nmap TARGET_IP`

---

# Nmap Command from the Notes

One command used in my notes is:

`nmap -v -sS -A -T4 TARGET_IP`

This combines several scan options.

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

Verbose mode displays more information while the scan is running.

Instead of waiting until the end of the scan, I can see more progress and discovery information.

A simple way to remember:

`-v = Show me more information`

---

# `-sS` — TCP SYN Scan

`-sS`

performs a:

`TCP SYN Scan`

It is also commonly called a:

`Half-Open Scan`

---

## Basic TCP SYN Scan Logic

A TCP connection normally begins with:

`SYN`

↓

`SYN/ACK`

↓

`ACK`

With a SYN scan, Nmap sends:

`SYN`

If the target returns:

`SYN/ACK`

Nmap can infer that the port is open.

The full TCP connection does not need to be completed.

Simplified:

`SYN`

↓

`SYN/ACK received`

↓

`Port appears open`

---

# `-A` — Aggressive Scan

The notes use:

`-A`

to enable several additional discovery features.

The notes associate this option with capabilities such as:

- Version detection
- Operating system detection
- Script scanning

A simple way to remember:

`-A = Gather more information about the target`

---

# Version Detection

Version detection attempts to determine which software version is running behind a network service.

Example concept:

`Port 80`

↓

`HTTP Service`

↓

`Apache`

↓

`Apache Version`

Knowing the service version can help an analyst understand the target environment.

---

# Operating System Detection

Nmap can also attempt to identify the target operating system.

For example:

`Windows`

or:

`Linux`

This is useful when building a basic understanding of the discovered system.

---

# Script Scanning

The notes mention Nmap script scanning as part of broader enumeration.

Nmap can use scripts to gather additional information about services.

The important concept for my current learning is:

`Open Port`

↓

`Service`

↓

`Additional Information`

---

# `-T4` — Timing

`-T4`

controls the scan timing.

In the notes, it is used to make scanning faster in appropriate lab environments.

The main concept is:

`Timing option → Controls how aggressively Nmap sends scan traffic`

---

# Reading Nmap Results

A basic Nmap result may contain columns such as:

`PORT`

`STATE`

`SERVICE`

Example concept:

| Port | State | Service |
|---|---|---|
| 21 | open | FTP |
| 22 | open | SSH |
| 80 | open | HTTP |

---

# Port State

The:

`STATE`

field tells me how Nmap interprets the port.

For example:

`open`

means a service appears to be accepting connections on that port.

---

# Service Identification

The:

`SERVICE`

column provides an estimate of which service is associated with the port.

Examples:

`21 → FTP`

`22 → SSH`

`80 → HTTP`

However, the port alone does not guarantee the service.

This is why service and version detection can provide additional information.

---

# Why Service Versions Matter

Two systems may both have:

`Port 80 open`

but they may run different software.

For example:

`System A`

→ Apache

`System B`

→ Nginx

The exact service and version provide more useful information than the port number alone.

---

# Basic Reconnaissance Workflow

A simple workflow from my notes can be organized as:

## Step 1 — Discover Devices

Use a network discovery tool to identify live devices.

Example concept:

`Netdiscover`

↓

`IP + MAC`

---

## Step 2 — Select a Target

Choose the system that belongs to the controlled lab.

Example:

`192.168.1.20`

---

## Step 3 — Scan the Target

Use Nmap to identify exposed network services.

Example structure:

`nmap TARGET_IP`

---

## Step 4 — Identify Ports

Determine which ports appear open.

Example:

`22/tcp open`

---

## Step 5 — Identify Services

Determine which services are associated with the open ports.

Example:

`22 → SSH`

---

## Step 6 — Identify Versions

When appropriate, identify the software versions.

This provides a better understanding of the system.

---

# Netdiscover vs Nmap

| Netdiscover | Nmap |
|---|---|
| Local network discovery | Network and service scanning |
| Finds IP/MAC relationships | Finds ports and services |
| Useful for identifying devices | More detailed target enumeration |
| Simpler discovery focus | More comprehensive reconnaissance |

The easiest way to remember:

`Netdiscover = Who is on the network?`

`Nmap = What is running on the device?`

---

# Network Discovery and Cybersecurity

Network discovery is important because security analysts first need visibility into the environment.

Without knowing which systems and services exist, it is difficult to evaluate security.

Discovery can help identify:

- Unknown devices
- Unexpected services
- Exposed ports
- Outdated services
- Systems that require further investigation

---

# Important Security Principle

Network scanning should only be performed on systems and networks where I have authorization.

These notes are based on:

- Cybersecurity courses
- Controlled labs
- CTF environments
- Authorized practice machines

---

# Quick Reference

| Tool / Option | Purpose |
|---|---|
| Netdiscover | Discover local network devices |
| `-i` | Select interface |
| `-r` | Define IP range |
| `-c` | Control request count |
| Nmap | Network mapper and service scanner |
| `-v` | Verbose output |
| `-sS` | TCP SYN scan |
| `-A` | Enable broader information gathering |
| `-T4` | Faster scan timing profile |
| Port | Identifies a network service endpoint |
| Service Detection | Identify service behind a port |
| Version Detection | Identify software version |

---

## Key Takeaway

The basic discovery process is:

`Find Devices → Find Ports → Identify Services → Identify Versions`

The easiest distinction is:

`Netdiscover → Who is there?`

`Nmap → What is running?`

This provides a foundation for later topics such as vulnerability assessment, network security testing, and service enumeration.
