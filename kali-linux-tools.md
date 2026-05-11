# Kali Linux Tools

## Network Interfaces

ifconfig = Shows information about network interfaces.

iwconfig = Shows detailed information about wireless interfaces.

Wireless interfaces can work in different modes.

## Managed Mode

Managed mode is used for normal Wi-Fi connection.

## Monitor Mode

Monitor mode is used to observe wireless network traffic in authorized lab environments.

## MAC Address Management

macchanger --help = Shows the help menu for macchanger.

macchanger --random <interface> = Changes the MAC address of a selected interface in a lab environment.

Note: MAC address changing should only be practiced in authorized environments.

## Airmon-ng

Airmon-ng is used to manage monitor mode on wireless interfaces.

airmon-ng start <interface> = Starts monitor mode on the selected interface.

airmon-ng stop <monitor-interface> = Stops monitor mode on the selected interface.

## Airodump-ng

Airodump-ng is used to observe wireless network information in monitor mode.

It can show information such as:
- BSSID
- Channel
- Encryption type
- Signal strength
- Connected clients

Note: This should only be used in authorized lab environments.

## Wireshark

Wireshark is a packet analysis tool. It is used to observe and analyze network traffic.

Wireshark can help understand:
- ARP traffic
- DNS requests
- TCP/IP packets
- HTTP traffic
- General network behavior

## Netdiscover

Netdiscover is used to discover devices in a local network.

It can help match:
- IP addresses
- MAC addresses

Example structure:
netdiscover -i <interface> -r <ip-range>

Parameters:
- -i = interface
- -r = IP range

## Nmap

Nmap is a network scanning tool. It can be used to discover hosts, services, and open ports in authorized environments.

Example structure:
nmap <target-ip-or-range>

Nmap is more comprehensive than basic discovery tools because it can also provide information about open ports and services.
