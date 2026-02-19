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

<img width="828" height="713" alt="Office Network" src="https://github.com/user-attachments/assets/a72f3984-5253-4e66-ad7b-aa4f0c803971" />

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
ipconfig/all

My PC Configuration:
- IPv4 Address: 172.20.6.132
- Subnet Mask: 255.255.255.0
- Default Gateway: 172.20.6.1
- DNS Server: 172.20.6.1
<img width="982" height="521" alt="IPCONFIG" src="https://github.com/user-attachments/assets/862f35a5-eb88-46b0-80eb-dd85b8fb7224" />

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
<img width="978" height="513" alt="Ping Default Gateway" src="https://github.com/user-attachments/assets/9ce020e3-fd74-4f2f-8aab-49bfae638e00" />

This confirmed LAN connectivity.

### Ping 8.8.8.8

result:
Packets Sent: 4 
Packets Received: 4 
Packet Loss:  0%
This tests the router's internet connection.
<img width="973" height="497" alt="ping 8 8 8 8" src="https://github.com/user-attachments/assets/58796a74-9274-4b14-9189-add256487ee6" />

### Ping google.com

result:
Packets Sent:  4
Packets Received:  4
Packet Loss:  0%
This tests the DNS resolution.
<img width="976" height="488" alt="ping google com" src="https://github.com/user-attachments/assets/3fc77d3f-0e82-43f5-a28d-389d32aa7b54" />

---

### Ping Other PC
Command:
ping 172.20.6.82

Initial Result:
Request timed out
<img width="980" height="511" alt="ping other PCS" src="https://github.com/user-attachments/assets/456d4277-5bcb-4c68-954e-d21c12f75791" />

---

## 5. Troubleshooting – Ping Failure Between PCs

### Issue Identified

While testing connectivity between PCs on the same network, other devices were unable to ping my PC (172.20.6.132). The error received was:

Request timed out

However:
- I was able to ping the default gateway.
- Both PCs were in the same subnet (172.20.6.0/24).
- Both PCs had valid IP addresses.
<img width="783" height="511" alt="ping Fail" src="https://github.com/user-attachments/assets/bd667408-7521-4c31-ae3a-278feb75f4bc" />

### Diagnosis Steps

1. Verified IP configuration using:
   ipconfig

2. Confirmed both devices were in the same network range:
   - My PC: 172.20.6.132
   - Other PC: 172.20.6.82
   - Subnet Mask: 255.255.255.0

3. Confirmed successful ping to the default gateway.
<img width="978" height="513" alt="Ping Default Gateway" src="https://github.com/user-attachments/assets/843a4738-d175-43c5-bd6c-95ccb793cd06" />

Since the network path was working, the issue was isolated to the destination machine (my PC).

### Root Cause

Windows Defender Firewall was blocking incoming ICMP (ping) requests.

By default, Windows blocks inbound ping requests for security reasons.

### Resolution

1. Opened Advanced Firewall Settings:
   - Pressed Windows + R
   - Typed: wf.msc
<img width="405" height="215" alt="WINDOWS + R" src="https://github.com/user-attachments/assets/79cb416d-4889-4294-b509-116c086a528f" />

2. Navigated to:
   Inbound Rules → File and Printer Sharing (Echo Request - ICMPv4-In)
<img width="1039" height="786" alt="Troubleshooting windows firewall" src="https://github.com/user-attachments/assets/97f9b686-8bd1-429b-a81c-e48384f89d5b" />

3. Enabled the rule for the Private profile.

After enabling the rule, the PCs were able to ping successfully.

## Outcome

The issue was resolved by allowing inbound ICMP traffic through Windows Firewall. This confirmed that the network infrastructure was functioning correctly and that the problem was the endpoint firewall configuration.
<img width="966" height="515" alt="Results after troubleshooting" src="https://github.com/user-attachments/assets/257441e2-ea80-4cf3-95a3-0b62d94903fa" />

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


