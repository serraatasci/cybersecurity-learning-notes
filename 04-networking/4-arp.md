# ARP — Address Resolution Protocol

This page contains my notes on ARP and the relationship between IP addresses and MAC addresses inside a local network.

---

## What Is ARP?

ARP stands for:

`Address Resolution Protocol`

ARP is used inside a local network to find the MAC address associated with an IP address.

A simple way to remember:

`IP Address → ARP → MAC Address`

---

# Why ARP Is Needed

When two devices communicate inside the same local network, the sender may know the destination IP address.

However, local network communication also needs the destination MAC address.

ARP helps solve this problem.

Example:

`192.168.1.20`

↓

`Which MAC address belongs to this IP?`

↓

`ARP`

↓

`00:11:22:33:44:55`

---

# IP and MAC Together

The two address types serve different purposes.

`IP Address`

→ Used for network-level addressing

`MAC Address`

→ Used for communication on the local network

ARP connects these two concepts.

Simplified:

`IP`

↓

`ARP Resolution`

↓

`MAC`

---

# Basic ARP Process

Imagine Computer A wants to communicate with:

`192.168.1.20`

but does not know the MAC address.

The simplified process is:

1. Computer A knows the target IP address.
2. Computer A asks the local network which device owns that IP.
3. The device with that IP responds with its MAC address.
4. Computer A stores the IP-to-MAC mapping.
5. Local communication can continue.

Conceptually:

`Who has 192.168.1.20?`

↓

`I have 192.168.1.20`

↓

`My MAC address is 00:11:22:33:44:55`

---

# ARP Request

An ARP Request is used when a device wants to learn which MAC address belongs to a specific IP address.

Simplified:

`Who has TARGET_IP?`

Because the sender does not yet know which device owns the IP address, the request is sent across the local network.

---

# ARP Reply

The device that owns the requested IP address responds with an ARP Reply.

Simplified:

`TARGET_IP belongs to my MAC address`

The sender can then use that MAC address for local communication.

---

# ARP Table

Devices do not need to repeat the ARP process for every packet.

Previously learned mappings can be stored temporarily in an:

`ARP Table`

or:

`ARP Cache`

Example concept:

| IP Address | MAC Address |
|---|---|
| `192.168.1.1` | `AA:BB:CC:11:22:33` |
| `192.168.1.20` | `00:11:22:33:44:55` |

The system can check this table before sending a new ARP request.

---

# Viewing ARP Information

On many systems, ARP-related information can be viewed using commands such as:

`arp`

The exact command and options can vary depending on the operating system.

The important concept is that the system maintains mappings between:

`IP addresses`

and:

`MAC addresses`

for local network communication.

---

# Example

Imagine:

`Laptop`

IP:

`192.168.1.10`

needs to communicate with:

`Server`

IP:

`192.168.1.50`

If the laptop does not know the server's MAC address:

`Laptop knows 192.168.1.50`

↓

`ARP Request`

↓

`Server responds with MAC address`

↓

`Laptop stores the mapping`

↓

`Local communication continues`

---

# ARP Works Inside the Local Network

ARP is primarily related to communication inside the same local network.

If the destination is on another network, the local device generally communicates with its router or default gateway.

In that case, the device may need the MAC address of the gateway rather than the final remote destination.

Simplified:

`My Computer`

↓

`Remote IP is outside my LAN`

↓

`Send traffic to Default Gateway`

↓

`Need Gateway MAC Address`

↓

`ARP`

---

# ARP and the Default Gateway

Suppose my computer wants to communicate with a remote Internet server.

The server is not inside my local network.

My computer sends the traffic toward the router.

Therefore, locally, it needs to know:

`Router IP → Router MAC Address`

ARP can be used to obtain this mapping.

---

# ARP vs DNS

ARP and DNS both perform a type of mapping, but they solve different problems.

`DNS`

→ Domain name to IP address

Example:

`google.com → IP`

`ARP`

→ IP address to MAC address

Example:

`192.168.1.1 → MAC`

A simple way to remember:

`DNS = Name → IP`

`ARP = IP → MAC`

---

# ARP vs Routing

ARP does not decide how traffic travels between different networks.

That is related to routing.

ARP is focused on local delivery.

Simplified:

`Routing`

→ Which network/path should traffic use?

`ARP`

→ Which local MAC address should receive the frame?

---

# Why ARP Matters in Cybersecurity

ARP is important because it helps explain how devices communicate inside a LAN.

Understanding ARP provides a foundation for topics such as:

- Local network discovery
- Packet analysis
- Network troubleshooting
- MAC addressing
- Man-in-the-middle concepts
- ARP spoofing

The security attack side of ARP is documented separately under the Network Security section.

---

# Basic Troubleshooting Logic

When investigating a local network issue, useful questions may include:

- Does the device have the correct IP address?
- Is the target on the same local network?
- Does the ARP table contain a MAC address for the destination?
- Is the correct default gateway being used?

ARP information can help understand whether local address resolution is working correctly.

---

# Quick Reference

| Term | Meaning |
|---|---|
| ARP | Address Resolution Protocol |
| ARP Request | Asks which MAC address owns an IP |
| ARP Reply | Returns the MAC address for the IP |
| ARP Table | Stores IP-to-MAC mappings |
| ARP Cache | Temporary stored ARP mappings |
| IP Address | Network-level address |
| MAC Address | Local network interface address |
| Default Gateway | Router used to reach other networks |

---

## Key Takeaway

The easiest way to remember ARP is:

`ARP = IP → MAC`

Inside a local network:

`I know the IP address`

↓

`I need the MAC address`

↓

`ARP Request`

↓

`ARP Reply`

↓

`IP-to-MAC mapping stored`

ARP is one of the key concepts that connects IP-level networking with local Ethernet communication.
