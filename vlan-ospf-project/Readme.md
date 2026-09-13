



Inter-VLAN Routing + Multi-Area OSPF Project

A Cisco Packet Tracer project demonstrating a small campus network with two core distribution switches, redundant links to access-layer switches, Inter-VLAN routing, Multi-Area OSPF, and DHCP services.


![topology Diagram](topology-Diagram.png)


Overview


2 Routers (R1, R2) — each connects to its own core switch via a routed link (Gig0/0):
R1: 10.1.1.0/24
R2: 10.1.2.0/24
2 Core/Distribution Switches (Gsw-1, Gsw-2) — interconnected with each other and dual-homed to every access switch below, providing redundant uplinks:
Gsw-1: Gig1/0/1–Gig1/0/6
Gsw-2: Gig1/0/1–Gig1/0/5
4 Access Switches (Sw1–Sw4) — each connects to both core switches for redundancy and hosts end devices on Fa0/1–Fa0/5:
Sw1: PC1, PC2, PC3
Sw2: PC4, PC5
Sw3: PC6, PC7, PC8
Sw4 (AS1): Server1, Server2
8 PCs and 2 Servers connected at the access layer.
Features Implemented
Inter-VLAN Routing — routing between VLANs across the core switches and routers.
Multi-Area OSPF — dynamic routing configured across multiple OSPF areas spanning R1 and R2.
DHCP Server — provides automatic IP addressing to end-host PCs.
Redundant Links — each access switch has dual uplinks to both core switches for fault tolerance.
Files
File	Description
*.pkt	Cisco Packet Tracer project file
network-diagram.png	Topology screenshot
README.md	This file
How to Use
Open the .pkt file in Cisco Packet Tracer.
Review device configurations (IP addressing, OSPF, VLANs, DHCP pools).
Use the simulation/PDU tools to verify end-to-end connectivity between PCs and servers across VLANs and OSPF areas.
Author

Riya Patel
