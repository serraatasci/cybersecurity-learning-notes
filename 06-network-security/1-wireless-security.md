# Wireless Security

This page contains my notes on wireless network monitoring, wireless interface modes, encryption types, and deauthentication concepts from controlled cybersecurity labs.

---

## Wireless Network Interfaces

Wireless adapters can operate in different modes.

The two modes covered in my notes are:

- Managed Mode
- Monitor Mode

---

# Managed Mode

Managed Mode is the normal operating mode of a Wi-Fi interface.

In this mode, the device connects to a wireless access point and uses the network normally.

Simplified:

`Wireless Adapter`

↓

`Access Point`

↓

`Network / Internet`

A simple way to remember:

`Managed Mode = Connect`

---

# Monitor Mode

Monitor Mode allows the wireless interface to observe wireless activity around it.

In this mode, the adapter is used for wireless monitoring rather than normal Wi-Fi access.

A simple way to remember:

`Monitor Mode = Observe`

---

# Managed Mode vs Monitor Mode

| Managed Mode | Monitor Mode |
|---|---|
| Normal Wi-Fi usage | Wireless monitoring |
| Connects to an access point | Observes wireless traffic |
| Used for normal network access | Used in analysis/security labs |

The easiest way to remember:

`Managed = Connect`

`Monitor = Observe`

---

# `iwconfig`

The command:

`iwconfig`

provides information related to wireless interfaces.

It can help display the current mode of a wireless interface.

For example, the wireless interface in my notes is:

`wlan0`

The mode may appear as:

`Managed`

or:

`Monitor`

---

# `airmon-ng`

`airmon-ng`

is used in my notes to manage Monitor Mode.

To start Monitor Mode:

`airmon-ng start wlan0`

After Monitor Mode is enabled, a new interface may appear as:

`wlan0mon`

Conceptually:

`wlan0`

↓

`Monitor Mode`

↓

`wlan0mon`

---

# Stopping Monitor Mode

To stop Monitor Mode:

`airmon-ng stop wlan0mon`

This returns the wireless adapter from the monitoring configuration toward normal use.

---

# `airodump-ng`

After the interface is placed into Monitor Mode, the notes use:

`airodump-ng wlan0mon`

The purpose is to collect information about nearby wireless networks.

A simple workflow is:

`Wireless Interface`

↓

`Monitor Mode`

↓

`airodump-ng`

↓

`Nearby Wireless Information`

---

# Information Collected During Wireless Monitoring

Wireless monitoring can provide information about nearby networks and devices.

Examples may include:

- Wireless access points
- Network identifiers
- MAC addresses
- Connected clients
- Wireless activity

This helps build an understanding of the surrounding wireless environment.

---

# Wireshark

My notes also mention:

`Wireshark`

Wireshark is used to observe and analyze network traffic.

In wireless security learning, captured traffic can be inspected to better understand how network communication works.

---

# Wireless Encryption

The wireless encryption methods mentioned in my notes are:

- WEP
- WPA
- WPA2

These technologies are used to protect wireless communication.

---

# WEP

WEP stands for:

`Wired Equivalent Privacy`

It is an older wireless security method.

The important point for my learning is that WEP represents an older generation of wireless protection.

---

# WPA

WPA stands for:

`Wi-Fi Protected Access`

It was introduced as an improvement over older wireless security mechanisms such as WEP.

---

# WPA2

WPA2 is a later version of WPA.

It is also used to protect wireless network communication.

A simple progression is:

`WEP`

↓

`WPA`

↓

`WPA2`

The main idea is that wireless security standards evolved over time to provide stronger protection.

---

# Why Wireless Encryption Matters

Wireless communication travels through radio signals.

Without protection, nearby devices may be able to observe wireless traffic.

Encryption helps protect the confidentiality of data traveling over the wireless network.

Conceptually:

`Wireless Traffic`

↓

`Encryption`

↓

`Protected Communication`

---

# Deauthentication

My notes also cover:

`Deauthentication`

This is a wireless concept where deauthentication frames are used to disconnect a client from an access point.

In the course lab, this was demonstrated with:

`aireplay-ng`

The key concept is:

`Client connected to Access Point`

↓

`Deauthentication frames`

↓

`Client connection interrupted`

---

# Why Deauthentication Matters in Security

Deauthentication is important because it shows that wireless management traffic can affect the connection state of clients.

It can cause:

- Temporary client disconnection
- Interruption of wireless communication
- Reconnection attempts

In security training, this helps demonstrate weaknesses that can exist in wireless management mechanisms.

---

# Targeting in a Controlled Lab

The notes explain that deauthentication can affect:

- An entire wireless network
- A specific client

This means the scope of the action can differ depending on the lab configuration.

Because this can interrupt real users, this type of testing should only be performed in controlled or explicitly authorized environments.

---

# Wireless Security Workflow

A simplified learning workflow from my notes is:

1. Identify the wireless interface
2. Check the interface mode
3. Enable Monitor Mode
4. Observe nearby wireless networks
5. Analyze wireless traffic
6. Study encryption and connection-management behavior
7. Return the interface to normal operation

---

# Why Monitor Mode Is Important

In normal Managed Mode:

`Adapter → Communicates as a Wi-Fi client`

In Monitor Mode:

`Adapter → Observes wireless activity`

This difference is important because many wireless security tools require Monitor Mode.

---

# Wireless Security and Cybersecurity

Understanding wireless networks helps explain security concepts such as:

- Wireless reconnaissance
- Network monitoring
- Traffic analysis
- Encryption
- Client authentication
- Connection management
- Wireless attack detection

---

# Controlled Lab Use

The commands and concepts in this section were learned in controlled cybersecurity labs.

Wireless security testing can disrupt network connectivity, so practical testing should only be performed on:

- Networks I own
- Authorized lab networks
- CTF environments
- Explicitly permitted systems

---

# Quick Reference

| Term / Tool | Meaning |
|---|---|
| Managed Mode | Normal Wi-Fi client mode |
| Monitor Mode | Wireless monitoring mode |
| `iwconfig` | View wireless interface information |
| `wlan0` | Wireless interface |
| `wlan0mon` | Monitor-mode interface |
| `airmon-ng` | Manage Monitor Mode |
| `airodump-ng` | Observe wireless network information |
| Wireshark | Analyze network traffic |
| WEP | Older wireless security mechanism |
| WPA | Wi-Fi Protected Access |
| WPA2 | Later WPA wireless security standard |
| Deauthentication | Disconnecting a wireless client from an AP |
| `aireplay-ng` | Tool used in the course's wireless lab |

---

## Key Takeaway

The easiest way to remember this section is:

`Managed Mode = Connect`

`Monitor Mode = Observe`

`airmon-ng = Change interface mode`

`airodump-ng = Observe nearby wireless networks`

`Wireshark = Analyze traffic`

`WEP / WPA / WPA2 = Wireless protection`

`Deauthentication = Interrupt a wireless client connection`

Wireless security builds directly on understanding network interfaces, MAC addresses, and local network communication.
