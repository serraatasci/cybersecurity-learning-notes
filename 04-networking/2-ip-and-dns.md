# IP Addresses and DNS

This page contains my notes on IP addresses, domain names, DNS, and basic connectivity checks.

---

## IP Address

An IP address is used to identify a device or network interface for communication on an IP network.

In my Linux notes, the command:

`ifconfig`

is used to view local network information, including the local IP address.

---

# Local IP Address

A local IP address identifies a device within its current network.

To view network interface information on Linux:

`ifconfig`

This can help me identify the IP address assigned to my machine.

---

# Domain Names

Humans usually access websites using names instead of IP addresses.

Example:

`google.com`

This is a:

`Domain Name`

Domain names are easier to remember than numeric IP addresses.

---

# DNS

DNS stands for:

`Domain Name System`

The main idea from my notes is:

`Domain Name ↔ IP Address`

For example:

`google.com`

is associated with an IP address through DNS.

A simple way to remember:

`DNS = Connects a domain name with an IP address`

---

# Why DNS Is Needed

When I type:

`google.com`

I use a human-readable name.

However, network communication ultimately needs an IP address.

Simplified:

`google.com`

↓

`DNS`

↓

`IP Address`

↓

`Network Communication`

---

# DNS and `ping`

The `ping` command can also be used with a domain name.

Example:

`ping google.com`

When the domain name is resolved, the command can display the IP address associated with it and send small network requests to the destination.

The command continues until it is stopped.

To stop it:

`Ctrl + C`

---

## Example Concept

`ping google.com`

can help demonstrate both:

- Domain name resolution
- Basic network connectivity

The simplified process is:

`google.com`

↓

`Resolve to IP`

↓

`Send ping requests`

↓

`Receive responses if available`

---

# IP Address vs Domain Name

The difference is:

`Domain Name`

→ Human-readable name

Example:

`google.com`

`IP Address`

→ Address used for network communication

DNS connects these two concepts.

---

# DNS and VPN

My notes also mention DNS in relation to VPN usage.

VPN stands for:

`Virtual Private Network`

The notes indicate that DNS configuration may sometimes also be changed when working with VPN-related network settings.

The two concepts are related to different parts of network communication:

`VPN`

→ Creates a virtual network connection

`DNS`

→ Maps domain names to IP addresses

VPN is covered separately in:

`vpn-basics.md`

---

# Basic Network Check

A simple workflow from my notes is:

1. Check my local IP information

`ifconfig`

2. Test a domain

`ping google.com`

3. Observe the resolved IP address and responses

4. Stop the command with:

`Ctrl + C`

---

# Why IP and DNS Matter in Cybersecurity

Understanding the relationship between IP addresses and domain names is important when examining network communication.

A basic investigation may involve identifying:

- Which IP address a system is using
- Which domain is being contacted
- Whether a hostname resolves to an IP address
- Whether basic communication with the destination works

---

# Quick Reference

| Term / Command | Meaning |
|---|---|
| IP Address | Address used for network communication |
| Local IP | IP assigned to a device on its network |
| Domain Name | Human-readable network name such as `google.com` |
| DNS | Connects domain names with IP addresses |
| `ifconfig` | Displays local network/interface information |
| `ping domain` | Sends connectivity requests and can show the resolved IP |
| `Ctrl + C` | Stops a running `ping` command |
| VPN | Virtual Private Network |

---

## Key Takeaway

The easiest way to remember DNS is:

`google.com → DNS → IP Address`

The domain name is easy for humans to remember, while the IP address is used for network communication.

For basic testing:

`ifconfig → Check my network information`

`ping google.com → Resolve the domain and test connectivity`
