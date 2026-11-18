# Project: Design and Configure a Multi-Branch Network Using Static Routing

## Project Overview

This project involves designing, configuring, and troubleshooting a multi-branch network for a fictional company, TechWorld Solutions, using Cisco Packet Tracer.

The company operates three office locations:
- Head Office (HQ)
- Lagos Branch
- Abuja Branch

Each location has its own Local Area Network (LAN), and all three branches are interconnected through Wide Area Network (WAN) links.

The primary objective was to establish communication between all three branches using static routing. The project also involved configuring default and floating static routes, performing connectivity tests, troubleshooting network issues, and expanding the network to accommodate an additional branch.

## Project Objectives

The objectives of this project were to:
- Design a multi-branch network topology using Cisco Packet Tracer.
- Configure router interfaces.
- Implement IPv4 addressing across LAN and WAN connections.
- Configure static routes to enable communication between remote networks.
- Understand next-hop addressing and routing table entries.
- Configure default and floating static routes.
- Verify connectivity between devices across different branches.
- Use network diagnostic commands to identify and resolve connectivity issues.
- Troubleshoot common routing and addressing problems.
- Expand the network by adding a fourth branch.

## Network Topology

The network consists of three interconnected office locations arranged in a linear topology.

### Network devices:
- 3 Cisco routers (2911 or 1941).
- 3 Cisco 2960 switches.
- 9 PCs (3 per branch).
- 3 WAN connections linking the routers.

### Router connections:
- R1 connects to R2.
- R2 connects to R3.
- R1 connects to R3.

Each router provides connectivity between its local LAN and the interconnected WAN network.

## IP Addressing Scheme

### LAN Addressing
| Router | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| R1 (HQ) | G0/2 | 192.168.10.1 | 255.255.255.0 |
| R2 (Lagos) | G0/0 | 192.168.20.1 | 255.255.255.0 |
| R3 (Abuja) | G0/0 | 192.168.30.1 | 255.255.255.0 |

### WAN Addressing
| Connection | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| R1–R2 | R1 G0/1 | 192.168.40.1 | 255.255.255.252 |
| R1–R2 | R2 G0/1 | 192.168.40.2 | 255.255.255.252 |
| R1–R3 | R1 G0/1 | 192.168.50.2 | 255.255.255.252 |
| R1–R3 | R3 G0/1 | 192.168.50.1 | 255.255.255.252 |
| R2–R3 | R2 G0/2 | 192.168.60.1 | 255.255.255.252 |
| R2–R3 | R3 G0/1 | 192.168.60.2 | 255.255.255.252 |


### PC Addressing
| PC | Branch | IP Address | Default Gateway |
|---|---|---|---|
| PC1 | HQ | 192.168.10.10 | 192.168.10.1 |
| PC2 | HQ | 192.168.10.11 | 192.168.10.1 |
| PC3 | HQ | 192.168.10.12 | 192.168.10.1 |
| PC4 | Lagos | 192.168.20.10 | 192.168.20.1 |
| PC5 | Lagos | 192.168.20.11 | 192.168.20.1 |
| PC6 | Lagos | 192.168.20.12 | 192.168.20.1 |
| PC7 | Abuja | 192.168.30.10 | 192.168.30.1 |
| PC8 | Abuja | 192.168.30.11 | 192.168.30.1 |
| PC9 | Abuja | 192.168.30.12 | 192.168.30.1 |

## Network Implementation

The network implementation involved the following activities:

1. Added three Cisco routers, three switches, and nine PCs to the Packet Tracer workspace.
2. Connected each branch's PCs to its local switch.
3. Connected each switch to its respective router.
4. Established WAN connections between the three routers.
5. Configured IPv4 addresses and subnet masks on router interfaces.
6. Configured IP addresses, subnet masks, and default gateways on all six PCs.
7. Enabled the router interfaces.
8. Configured static routes to provide connectivity between remote LANs.

Router interface configuration example:

enable
configure terminal

interface gigabitEthernet 0/2
ip address 192.168.10.1 255.255.255.0
no shutdown

interface gigabitEthernet 0/1
ip address 192.168.50.2 255.255.255.252
no shutdown

Interface names may vary depending on the router model used.

## Static Routing Configuration

Static routing was implemented to enable communication between the different branch networks.

The Cisco IOS static route command follows this syntax:
ip route DESTINATION_NETWORK SUBNET_MASK NEXT_HOP_IP

### R1 – Head Office

ip route 192.168.20.0 255.255.255.0 192.168.40.2

ip route 192.168.30.0 255.255.255.0 192.168.50.1

### R2 – Lagos Branch

ip route 192.168.10.0 255.255.255.0 192.168.40.

ip route 192.168.30.0 255.255.255.0 192.168.60.2

### R3 – Abuja Branch

ip route 192.168.10.0 255.255.255.0 192.168.50.2

ip route 192.168.20.0 255.255.255.0 192.168.60.1

These routes provide paths to remote LANs through the appropriate next-hop addresses.

## Verification and Testing

Several Cisco IOS commands and connectivity tests were used to examine the network configuration and verify communication.

### Verification Commands

| Command| Purpose |
|---|---|---|
| "show ip interface brief"| Check interface IP addresses and status |
| "show ip route"| Examine the routing table |
| "show running-config"| Review active router configurations |
| "show interfaces"| Inspect interface status and statistics |
| "ping"| Test connectivity between devices |
| "traceroute"| Identify the path packets take between routers |
| "tracert"| Trace the path from a PC |


### Connectivity Tests

The following connectivity tests were performed:
- PC1 pinging its default gateway.
- PC1 communicating with PC3.
- PC1 communicating with PC5.
- PC5 communicating with PC1.
- PC5 communicating with PC3.
- Tracing the path from PC1 to PC5.

These tests helped verify communication between devices within different branch networks and examine the routing path across the network.

## Troubleshooting

Six deliberate troubleshooting challenges were performed to develop practical troubleshooting and problem-solving skills.

| No. | Troubleshooting Challenge | Objective |
|---|---|---|
| 1 | Remove a static route from R1 | Identify missing routes affecting remote network connectivity |
| 2 | Change R2's WAN IP address | Identify IP addressing inconsistencies between connected routers |
| 3 | Shut down R3's LAN interface | Identify interface availability issues |
| 4 | Configure an incorrect default gateway on PC5 | Understand the effect of incorrect gateway configuration |
| 5 | Configure an incorrect subnet mask on R1 | Identify subnetting and addressing problems |
| 6 | Remove the return route from R3 | Understand the importance of bidirectional routing |


For each challenge, the troubleshooting process involved:

1. Identifying the connectivity problem.
2. Determining the affected device or network.
3. Using appropriate diagnostic commands.
4. Examining the relevant configurations.
5. Correcting the identified issue.
6. Retesting connectivity.

These exercises provided practical experience in identifying routing, interface, and IP addressing problems.

## Key Concepts Learned

Through this project, I developed practical experience and a better understanding of:
- Static routing and manual route configuration.
- Next-hop IP addressing.
- IPv4 addressing and subnet masks.
- LAN and WAN network design.
- Directly connected and remote networks.
- Routing tables and route selection.
- Default static routes.
- Floating static routes and administrative distance.
- Inter-network communication.
- The importance of return routes in bidirectional communication.
- Network verification and troubleshooting.
- Using Cisco IOS diagnostic commands.
- Expanding an existing network infrastructure.

## Project Files

The following folders contain the supporting project files and documentation.

| Folder | Description |
|---|---|
| "topology/" (topology/)| Network topology diagram |
| "screenshots/" (screenshots/)| Configuration and connectivity screenshots |
| "packet-tracer/" (packet-tracer/)| Cisco Packet Tracer project file |

## Conclusion

This project provided practical experience in designing, configuring, and troubleshooting a multi-branch network using static routing in Cisco Packet Tracer.

By connecting three office locations and enabling communication between their respective LANs, I gained a better understanding of how routers forward packets between remote networks using manually configured routes.

The troubleshooting exercises helped strengthen my ability to identify and resolve common network connectivity issues, while the bonus challenges introduced additional routing concepts, including default static routes, floating static routes, and network expansion.

This project forms part of my ongoing journey towards becoming a network engineer and preparing for the Cisco Certified Network Associate (CCNA) certification.
