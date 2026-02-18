# Network-Mapping
Network Mapping and Connectivity Testing project demonstrating IP configuration analysis, ping testing, and firewall troubleshooting within a workplace LAN environment.
# Network Mapping and Connectivity Testing Project

## 1. Project Overview

This project demonstrates practical networking skills, including:
- Identifying IP configuration
- Mapping a workplace network
- Testing connectivity using ping
- Troubleshooting network communication issues

Course: The Bits and Bytes of Computer Networking  
Duration: 2 Days  
Focus Areas: TCP/IP, DNS, Routing, Network Layers

---

## 2. Network Topology Diagram

![Workplace Network Diagram]((https://capeitinitiative-my.sharepoint.com/:b:/g/personal/jabulile_ngomane_capaciti_org_za/IQAD_YRJSgX4R5H3H4pEz49oAblnHaqA0-b-WP89AVxz_3o?e=S9wdLk))

Description:
The network consists of:
- Internet (ISP)
- Router
- Firewall
- Switch
- 3 Desktop PCs
- Wireless Access Point (WAP)
- Laptop and Mobile Device

Traffic flows from end devices → Switch → Firewall → Router → Internet.

---

## 3. IP Configuration Results

Command Used:
ipconfig

My PC Configuration:
- IPv4 Address: 172.20.6.132
- Subnet Mask: 255.255.255.0
- Default Gateway: 172.20.6.1
- DNS Server: (add yours)

All devices were confirmed to be in the same subnet (172.20.6.0/24).

---

## 4. Ping Test Results

### Ping Default Gateway
Command:
ping 172.20.6.1

Result:
Packets Sent: 4  
Packets Received: 4  
Packet Loss: 0%  

This confirmed LAN connectivity.

### Ping 8.8.8.8
Packets Sent: 4 
Packets Received: 4 
Packet Loss:  0%

### Ping google.com
Packets Sent:  4
Packets Received:  4
Packet Loss:  0%

---

### Ping Other PC
Command:
ping 172.20.6.82

Initial Result:
Request timed out

---

## 5. Troubleshooting – Ping Failure Between PCs

### Issue Identified

While testing connectivity between PCs on the same network, other devices were unable to ping my PC (172.20.6.132). The error received was:

Request timed out

However:
- I was able to ping the default gateway.
- Both PCs were in the same subnet (172.20.6.0/24).
- Both PCs had valid IP addresses.

### Diagnosis Steps

1. Verified IP configuration using:
   ipconfig

2. Confirmed both devices were in the same network range:
   - My PC: 172.20.6.132
   - Other PC: 172.20.6.82
   - Subnet Mask: 255.255.255.0

3. Confirmed successful ping to the default gateway.

Since the network path was working, the issue was isolated to the destination machine (my PC).

### Root Cause

Windows Defender Firewall was blocking incoming ICMP (ping) requests.

By default, Windows blocks inbound ping requests for security reasons.

### Resolution

1. Opened Advanced Firewall Settings:
   - Pressed Windows + R
   - Typed: wf.msc

2. Navigated to:
   Inbound Rules → File and Printer Sharing (Echo Request - ICMPv4-In)

3. Enabled the rule for the Private profile.

After enabling the rule, the PCs were able to ping successfully.

## Outcome

The issue was resolved by allowing inbound ICMP traffic through Windows Firewall. This confirmed that the network infrastructure was functioning correctly and that the problem was endpoint firewall configuration.

## 6. Networking Concepts Demonstrated

- IPv4 Addressing
- Subnetting (/24 network)
- Default Gateway Function
- ICMP Protocol
- Windows Firewall Configuration
- LAN Troubleshooting Methodology
- OSI Layer 3 (Network Layer)
- TCP/IP Model

---

## 7. Skills Demonstrated

- Command Line Usage
- Network Diagnostics
- Problem Isolation
- Firewall Configuration
- Technical Documentation
- Structured Troubleshooting

---

## 8. Conclusion

This project successfully demonstrated the ability to map a workplace network, test connectivity, and resolve a firewall-related ICMP issue using professional troubleshooting methodology.


