# MAC Addresses and Network Interfaces

This page contains my notes on MAC addresses, Linux network interfaces, wireless interfaces, and basic interface modes.

---

## What Is a MAC Address?

MAC stands for:

`Media Access Control`

A MAC address is a hardware-related address associated with a network interface.

In my notes, a MAC address is described as:

- 48 bits long
- Written using 12 hexadecimal digits

Example:

`00:1A:2B:3C:4D:5E`

A MAC address helps devices identify each other on a local network.

---

# MAC Address Format

A MAC address commonly looks like:

`00:1A:2B:3C:4D:5E`

It contains six groups of hexadecimal values.

Hexadecimal uses:

`0-9`

and:

`A-F`

---

# MAC Address vs IP Address

A useful distinction is:

`MAC Address`

→ Used for local network communication

`IP Address`

→ Used for communication across IP networks

Both can be associated with the same network interface.

---

# Network Interface

A network interface is the connection point used by a device to communicate with a network.

Examples can include:

- Ethernet interface
- Wireless interface

In Linux wireless labs, the interface in my notes is:

`wlan0`

---

# `wlan0`

`wlan0`

is the wireless network interface used in the lab notes.

Commands can target this interface to:

- View wireless information
- Disable or enable the interface
- Change its mode
- Inspect wireless networks

---

# `ifconfig`

The command:

`ifconfig`

can display network interface information.

In my notes, it is used to check information such as:

- Local IP address
- Network interfaces

It can also be used to change the state of an interface.

---

# Disabling a Wireless Interface

Before changing certain interface properties, the wireless interface may be brought down.

Example from my notes:

`ifconfig wlan0 down`

This disables the interface temporarily.

---

# Enabling the Wireless Interface

After making changes, the interface can be brought back up.

Conceptually:

`Interface Down`

↓

`Make Configuration Change`

↓

`Interface Up`

The standard idea is to reactivate the interface after the change is complete.

---

# `macchanger`

`macchanger`

is a tool used to change the MAC address associated with an interface.

To view help information:

`macchanger --help`

This displays usage information for the tool.

---

# Random MAC Address

The notes include changing the MAC address of:

`wlan0`

to a random value.

The general idea is:

`Original MAC Address`

↓

`Interface disabled`

↓

`MAC address changed`

↓

`Interface enabled again`

---

# Why MAC Addresses May Be Changed

In controlled security labs, changing a MAC address can be useful for understanding:

- Network interface identity
- MAC-based filtering
- Local network behavior
- Privacy concepts

The important concept is that the MAC address seen by the local network can be modified through software in some environments.

---

# `iwconfig`

`iwconfig`

provides information specifically related to wireless network interfaces.

Compared with general network tools, it focuses more on wireless configuration.

It can show information such as:

- Wireless interface
- Wireless mode
- Connection information

---

# Wireless Interface Modes

The two wireless modes covered in my notes are:

- Managed Mode
- Monitor Mode

---

# Managed Mode

In Managed Mode, the wireless interface behaves like a normal Wi-Fi client.

The device can connect to a wireless access point and use the network normally.

Simplified:

`Wireless Adapter`

↓

`Access Point`

↓

`Network / Internet`

A simple way to remember:

`Managed Mode = Normal Wi-Fi connection`

---

# Monitor Mode

Monitor Mode allows the wireless interface to observe wireless traffic in the surrounding environment.

The interface does not behave like a normal connected Wi-Fi client.

Instead, it can be used to inspect nearby wireless activity in controlled security labs.

A simple way to remember:

`Monitor Mode = Observe wireless traffic`

---

# Managed Mode vs Monitor Mode

| Managed Mode | Monitor Mode |
|---|---|
| Normal Wi-Fi usage | Wireless monitoring |
| Connects to an access point | Observes nearby wireless traffic |
| Used for normal network access | Used for analysis and security labs |

The easiest way to remember:

`Managed = Connect`

`Monitor = Observe`

---

# `airmon-ng`

The notes use:

`airmon-ng`

to help place a wireless interface into Monitor Mode.

Example concept:

`wlan0`

↓

`Monitor Mode`

↓

`wlan0mon`

The new interface name may appear as:

`wlan0mon`

after Monitor Mode is enabled.

---

# Stopping Monitor Mode

When the wireless monitoring work is finished, Monitor Mode can be stopped.

The interface can then be returned to normal wireless operation.

Conceptually:

`Monitor Mode`

↓

`Stop monitoring`

↓

`Return to normal interface mode`

---

# `airodump-ng`

After the wireless interface is placed into Monitor Mode, the notes use:

`airodump-ng`

to collect information about nearby wireless networks.

The command operates on the monitor-mode interface.

Example concept:

`Monitor Interface`

↓

`airodump-ng`

↓

`Nearby wireless network information`

---

# Information from Wireless Monitoring

The notes use wireless monitoring to gather information about nearby networks.

This can help identify items such as:

- Wireless access points
- Network identifiers
- MAC addresses
- Nearby clients
- Wireless activity

These topics are explored further under the Network Security section.

---

# Why This Matters in Cybersecurity

Understanding MAC addresses and wireless interfaces helps explain:

- How devices identify themselves on a LAN
- How local network communication works
- How wireless adapters operate
- Why wireless interfaces can have different modes
- How wireless traffic can be observed during authorized security testing

---

# Controlled Lab Use

The wireless tools in these notes were used in controlled cybersecurity learning environments.

The purpose was to understand wireless networking behavior and security concepts.

---

# Quick Reference

| Term / Command | Purpose |
|---|---|
| MAC Address | Local network interface address |
| 48-bit | Length of a standard MAC address |
| Hexadecimal | Number format used in MAC addresses |
| `wlan0` | Wireless network interface |
| `ifconfig` | View/manage interface information |
| `iwconfig` | View wireless interface information |
| `macchanger` | Change a MAC address |
| Managed Mode | Normal Wi-Fi client mode |
| Monitor Mode | Wireless monitoring mode |
| `airmon-ng` | Manage monitor mode |
| `wlan0mon` | Common monitor-mode interface name |
| `airodump-ng` | Collect wireless network information |

---

## Key Takeaway

The most important concepts are:

`MAC Address = Local network identity`

`wlan0 = Wireless interface`

`Managed Mode = Connect`

`Monitor Mode = Observe`

Understanding these concepts provides a foundation for later wireless security and network monitoring topics.
