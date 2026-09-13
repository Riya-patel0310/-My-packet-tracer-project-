
##**Inter-VLAN Routing + Multi-Area OSPF + DHCP Server**



A Cisco Packet Tracer project simulating a multi-area OSPF network connecting three sites (Network1, Network2, Network3), each segmented into multiple VLANs, plus a central server reachable from all areas.
 
  


![Network Diagram](network-diagram.png)



** Overview**

## Topology Overview

- **R1 (ISR4331)** — connects **Network1** to the backbone.
  - **Gig0/0/1** → **SW1 (Network1)**, `10.1.1.0/24`, **OSPF Area 1**
  - **Se0/2/0** → **R2**, `10.2.2.0/24`, **OSPF Area 0**

- **R2 (Central Router)** — backbone router linking all three networks and the server.
  - **Gig0/0/1** → **Server S1**, `10.5.5.0/30`
  - **Gig0/0/0** → **SW3 (Network3)**, **OSPF Area 1**
  - **Se0/2/0** → **R1**, **OSPF Area 0**
  - **Se0/2/1** → **R3**, `10.3.3.0/24`, **OSPF Area 0**

- **R3 (ISR4331)** — connects **Network2** to the backbone.
  - **Gig0/0/1** → **SW2 (Network2)**, `10.4.4.0/24`, **OSPF Area 2**
  - **Se** → **R2**, **OSPF Area 0**
 
  ### OSPF Areas

| Area | Scope |
|---|---|
| Area 0 (Backbone) | R1 ↔ R2 ↔ R3 serial links |
| Area 1 | Network1 (via R1) and Network3 (via R2) |
| Area 2 | Network2 (via R3) |


## Networks & VLANs

**Network1** (via SW1)

| VLAN | Subnet | Gateway | Hosts |
|---|---|---|---|
| VLAN 10 | `192.168.10.0/24` | `192.168.10.1` | PC0, PC1 |
| VLAN 20 | `192.168.20.0/24` | `192.168.20.1` | PC2, PC3 (via multilayer switch1) |

**Network2** (via SW2)

| VLAN | Subnet | Gateway | Hosts |
|---|---|---|---|
| VLAN 30 | `192.168.30.0/24` | `192.168.30.1` | PC4, PC5 |
| VLAN 40 | `192.168.40.0/24` | `192.168.40.1` | PC6, PC7 |

**Network3** (via SW3)

| VLAN | Subnet | Gateway | Hosts |
|---|---|---|---|
| VLAN 50 | `192.168.50.0/24` | `192.168.50.1` | PC11, PC12 |
| VLAN 60 | `192.168.60.0/24` | `192.168.60.1` | PC13, PC14 |

## Features Implemented

- **Multi-Area OSPF** — Area 0 backbone between the three routers, with Area 1 and Area 2 handling the site LANs, keeping routing tables smaller and updates localized per area.
- **VLAN Segmentation** — Each network is split into two VLANs, each with its own gateway/subnet.
- **Centralized Server Access** — A server (S1) attached to the backbone router (R2) is reachable from every VLAN/area via OSPF.
- **Inter-VLAN Routing** — Multilayer switching is used at Network1 to route between VLAN 10 and VLAN 20 locally.

## Files

| File | Description |
|---|---|
| `*.pkt` | Cisco Packet Tracer project file |
| `network-diagram.png` | Topology screenshot |
| `README.md` | Project documentation |


## How to Use

1. **Open the `.pkt` file** in Cisco Packet Tracer.
2. **Review each router's OSPF configuration** (`router ospf`, `network` statements per area) and **VLAN/SVI setup** on the switches.
3. Use **`show ip ospf neighbor`** and **`show ip route`** to confirm area adjacencies and inter-area routes, then **`ping`/PDUs** to verify end-to-end connectivity across all VLANs and to the server.

## References

- **Learned from the YouTube channel:** **The Last Hop Tech**

## Author

**Riya Patel**
