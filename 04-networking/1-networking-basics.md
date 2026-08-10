# Networking Basics

This page contains my notes on basic networking concepts and connectivity testing.

---

## What Is a Computer Network?

A computer network is a group of devices that can communicate with each other.

Devices on a network can include:

- Computers
- Servers
- Phones
- Routers
- Printers
- IoT devices

A network allows these devices to exchange data and share resources.

---

# Basic Communication Model

A simple network communication can be represented as:

`Device A`

↓

`Network`

↓

`Device B`

For example:

`Laptop`

↓

`Router`

↓

`Web Server`

↓

`Website Response`

The devices need addressing and communication rules in order to exchange information successfully.

---

# LAN — Local Area Network

LAN stands for:

`Local Area Network`

A LAN connects devices within a relatively small area.

Examples include:

- Home network
- School computer lab
- Office
- Company floor

Common LAN technologies include:

- Ethernet
- Wi-Fi

Example:

`Laptop + Phone + Printer + Router`

can all belong to the same home LAN.

---

# WAN — Wide Area Network

WAN stands for:

`Wide Area Network`

A WAN connects devices or networks across a much larger geographical area.

A simple comparison is:

`LAN → Small local area`

`WAN → Large geographical area`

The Internet is the most familiar example of interconnected networks on a global scale.

---

# Internet vs Local Network

A local network allows nearby devices to communicate with each other.

The Internet connects many different networks together.

Simplified:

`Computer`

↓

`Local Network`

↓

`Router`

↓

`Internet`

↓

`Remote Network / Server`

---

# Router

A router connects different networks and forwards traffic between them.

For example, a home router can connect:

`Home LAN`

to:

`Internet`

Simplified:

`Local Device`

↓

`Router`

↓

`Another Network`

Routers primarily make forwarding decisions using IP addresses.

---

# Switch

A switch connects devices inside a local network.

For example:

`Computer 1`

`Computer 2`

`Server`

↓

`Switch`

The switch helps these devices communicate within the LAN.

A useful basic distinction is:

`Switch → Communication inside a LAN`

`Router → Communication between networks`

---

# Client and Server

Many network applications use the:

`Client-Server`

model.

The client requests a service.

The server provides the service.

Example:

`Web Browser`

↓

`Request`

↓

`Web Server`

↓

`Response`

Here:

- Browser → Client
- Web server → Server

---

# Example: Opening a Website

When I open a website, several networking concepts work together.

Simplified workflow:

`Browser`

↓

`Find server address`

↓

`Connect to server`

↓

`Send request`

↓

`Server sends response`

↓

`Browser displays website`

Later notes cover the individual technologies involved in this process, such as:

- DNS
- IP addresses
- Ports
- TCP
- HTTP / HTTPS

---

# IP Address

An IP address identifies a device or network interface for communication across IP networks.

Example:

`192.168.1.10`

The IP address helps network traffic reach the correct destination.

A simple way to think about it is:

`IP Address = Network address`

IP addressing is covered in more detail in:

`ip-and-dns.md`

---

# MAC Address

A MAC address identifies a network interface at the local network level.

Example format:

`00:1A:2B:3C:4D:5E`

A simple distinction is:

`IP → Used for communication across networks`

`MAC → Used for local network communication`

MAC addresses are covered separately in:

`mac-addresses-and-interfaces.md`

---

# Protocol

A protocol is a set of rules that devices follow when communicating.

Different protocols have different purposes.

Examples include:

- HTTP / HTTPS
- DNS
- SSH
- FTP
- TCP
- UDP
- ICMP

A simple way to remember:

`Protocol = Communication rules`

---

# Ports

A computer can run multiple network services at the same time.

Ports help identify which service or application network traffic belongs to.

Example concept:

`Server IP`

↓

`Port`

↓

`Specific Service`

For example, SSH commonly uses:

`Port 22`

Ports and protocols are covered separately in:

`ports-and-protocols.md`

---

# `ping`

`ping` is a basic command used to test whether another device can be reached over an IP network.

Example:

`ping 8.8.8.8`

Another example:

`ping example.com`

---

## What Does Ping Tell Me?

Ping can help determine whether:

- A host appears reachable
- Network communication is working
- Responses are being received
- There may be connectivity problems

Simplified:

`My Computer`

↓

`Ping Request`

↓

`Target`

↓

`Ping Response`

---

# ICMP

Ping commonly uses:

`ICMP`

which stands for:

`Internet Control Message Protocol`

ICMP is used for network control and diagnostic messages.

Ping uses ICMP messages to test connectivity.

---

# Ping Does Not Prove Everything

A system that does not respond to ping is not automatically offline.

ICMP traffic may be:

- Blocked by a firewall
- Disabled
- Filtered by network rules

Therefore:

`No Ping Response ≠ Definitely Offline`

This becomes important during network troubleshooting and security testing.

---

# Domain Names

Humans usually prefer names such as:

`google.com`

instead of remembering IP addresses.

DNS helps translate domain names into IP addresses.

Simplified:

`google.com`

↓

`DNS`

↓

`IP Address`

DNS is covered separately in:

`ip-and-dns.md`

---

# Network Interfaces

A device connects to a network through a network interface.

Examples include:

- Ethernet adapter
- Wi-Fi adapter
- Virtual network adapter

On Linux, network interface information can be inspected using tools such as:

`ifconfig`

The interface may have information such as:

- IP address
- MAC address
- Network status

---

# Basic Connectivity Troubleshooting

When a network connection is not working, I can think through the problem step by step.

Example workflow:

1. Check whether the network interface is active
2. Check the IP address
3. Test local connectivity
4. Test the gateway
5. Test a remote IP address
6. Check DNS resolution

For example:

`ping TARGET_IP`

can help test basic IP connectivity.

---

# Private Networks

Devices inside home or company networks commonly use private IP addresses.

Common examples may look like:

`192.168.x.x`

`10.x.x.x`

These addresses are commonly used inside internal networks.

The router then connects the private network to external networks such as the Internet.

---

# Cybersecurity Perspective

Networking knowledge is essential in cybersecurity because attacks and security monitoring often involve communication between systems.

Understanding networking helps with:

- Identifying devices
- Understanding network traffic
- Finding exposed services
- Analyzing suspicious connections
- Reading firewall logs
- Network reconnaissance
- Packet analysis

---

# Controlled Lab Practice

In my cybersecurity labs, networking concepts are used to understand communication between:

`Attack / Testing Machine`

and:

`Target Machine`

For example:

`AttackBox`

↓

`Lab Network`

↓

`Target Machine`

Before working with a target service, I first need to understand how the two systems communicate.

All testing in these notes is performed in controlled or authorized lab environments.

---

# Basic Networking Workflow

A simple workflow is:

`Identify Target`

↓

`Check Connectivity`

↓

`Identify Network Address`

↓

`Identify Available Services`

↓

`Analyze Communication`

Different tools are used at each stage.

Later sections cover tools such as:

- Nmap
- Netdiscover
- Wireshark

---

# Important Distinctions

## IP vs MAC

`IP`

→ Network-level addressing

`MAC`

→ Local network interface addressing

---

## Switch vs Router

`Switch`

→ Connects devices inside a LAN

`Router`

→ Connects different networks

---

## Client vs Server

`Client`

→ Requests a service

`Server`

→ Provides a service

---

## LAN vs WAN

`LAN`

→ Small local network

`WAN`

→ Large geographical network

---

# Quick Reference

| Term | Meaning |
|---|---|
| Network | Connected devices that communicate |
| LAN | Local Area Network |
| WAN | Wide Area Network |
| Router | Connects different networks |
| Switch | Connects devices within a LAN |
| Client | Requests a service |
| Server | Provides a service |
| IP Address | Network-level address |
| MAC Address | Local network interface address |
| Protocol | Rules for network communication |
| Port | Identifies a network service/application |
| `ping` | Basic connectivity test |
| ICMP | Network control and diagnostic protocol |
| DNS | Translates domain names to IP addresses |

---

## Key Takeaway

The basic networking idea is:

`Devices → Addresses → Network → Protocols → Communication`

For cybersecurity, I first need to understand:

`Who is communicating with whom?`

`Which address is being used?`

`Which service is running?`

`How is the traffic moving through the network?`

These fundamentals provide the foundation for later topics such as ARP, Nmap, network discovery, and traffic analysis.
