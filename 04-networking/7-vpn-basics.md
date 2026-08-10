# VPN Basics

This page contains my basic notes on VPN connections and OpenVPN usage.

---

## What Is a VPN?

VPN stands for:

`Virtual Private Network`

A VPN creates a virtual network connection between my device and another network.

In cybersecurity labs, VPN connections are commonly used to connect my own machine to a controlled lab network.

A simple way to remember:

`My Computer`

↓

`VPN Connection`

↓

`Remote / Lab Network`

---

# Why VPN Is Useful

A VPN allows my computer to communicate with systems that are available through the VPN network.

In a lab environment, this can make remote target machines reachable from my own computer.

Conceptually:

`Local Computer`

↓

`VPN`

↓

`Lab Network`

↓

`Target Machine`

---

# OpenVPN

The tool used in my notes is:

`OpenVPN`

A VPN connection can be started using an OpenVPN configuration.

General structure:

`openvpn CONFIG_FILE`

The exact configuration file depends on the VPN environment being used.

---

# Connecting to a VPN

The basic workflow is:

1. Obtain the VPN configuration
2. Start OpenVPN
3. Wait for the connection to establish
4. Access systems available through the VPN network

Simplified:

`VPN Configuration`

↓

`OpenVPN`

↓

`VPN Connected`

↓

`Remote Network Accessible`

---

# Stopping the VPN Connection

When OpenVPN is running in the terminal, the connection can be stopped with:

`Ctrl + C`

This terminates the running OpenVPN process.

---

# VPN and DNS

My notes also mention DNS in relation to VPN usage.

DNS stands for:

`Domain Name System`

DNS connects domain names with IP addresses.

Example:

`google.com`

↓

`DNS`

↓

`IP Address`

The notes mention that DNS configuration may sometimes also need to be changed when working with VPN-related network settings.

---

# VPN vs DNS

These two technologies have different purposes.

`VPN`

→ Creates a virtual network connection

`DNS`

→ Resolves domain names to IP addresses

They may both affect how network communication works, but they solve different problems.

---

# VPN in Cybersecurity Labs

VPNs are commonly useful in controlled cybersecurity environments because they provide access to isolated lab networks.

A typical workflow can look like:

`My Machine`

↓

`OpenVPN`

↓

`Cybersecurity Lab Network`

↓

`Target IP`

After connecting, normal networking tools can be used against authorized lab systems.

Examples may include:

- `ping`
- SSH
- Nmap

---

# Connectivity Check

After connecting to a VPN, a basic connectivity test may be performed.

Example:

`ping TARGET_IP`

This can help check whether the target appears reachable through the VPN network.

However:

`No ping response ≠ Target is definitely offline`

because ICMP traffic may be filtered or blocked.

---

# VPN and Security

The important concept from my learning is that VPN provides a virtual network connection.

In security labs, this allows my computer to securely participate in the lab network instead of exposing the lab environment directly to the public Internet.

---

# Quick Reference

| Term / Command | Meaning |
|---|---|
| VPN | Virtual Private Network |
| OpenVPN | Tool used to establish VPN connections |
| `openvpn CONFIG_FILE` | Start an OpenVPN connection |
| `Ctrl + C` | Stop the running OpenVPN connection |
| DNS | Domain Name System |
| `ping TARGET_IP` | Basic connectivity test |

---

## Key Takeaway

The easiest way to remember VPN is:

`VPN = Virtual connection to another network`

In my lab workflow:

`My Computer → OpenVPN → Lab Network → Target Machine`

DNS is a separate concept:

`Domain Name → DNS → IP Address`
