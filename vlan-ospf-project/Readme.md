
Multi-Site WAN with VLANs and DHCP Relay

A Cisco Packet Tracer project simulating a 3-site WAN (Dallas, Austin, and a third branch site) with VLAN segmentation, inter-VLAN routing via router sub-interfaces, and DHCP relay between sites.



![topology Diagram](topology-Diagram.png)


## Sites & Topology

- **Dallas Router (R-Dallas)** — central site, connects to:
  - A local switch trunking three VLANs via **router sub-interfaces**
  - **Austin site (R1)** over a serial WAN link
  - **Third branch site router** over a serial WAN link

- **Austin Router (R1)** — connects to a switch serving two VLANs (**Austin-LAN1** and **Austin-LAN2**), linked back to Dallas.

- **Branch Router** — connects to a switch serving two more VLANs, linked to Dallas.

 ## WAN Links (Serial)

| Link | Subnet |
|---|---|
| Dallas ↔ Austin (R1) | `2.2.2.0/30` |
| Dallas ↔ Branch Router | `1.1.1.0/30` |
| Austin (R1) ↔ Branch Router | `3.3.3.0/30` |



## VLANs

| VLAN | Site | Subnet | Ports | Notes |
|---|---|---|---|---|
| VLAN 10 | Dallas | `192.168.10.0/24` | `Fa0/1–7` | |
| VLAN 20 (IT) | Dallas | `192.168.20.0/24` | `Fa0/8–14` | |
| VLAN 30 | Dallas | `192.168.30.0/24` | `Fa0/15–24` | Hosts Server2 (`icca.com`), DNS server |
| VLAN 60 | Austin-LAN1 | — | `Fa0/1–14` | DHCP relay from Houston |
| VLAN 70 | Austin-LAN2 | `192.168.70.0/24` | `Fa0/15–24` | DHCP relay from Dallas |
| VLAN 40 | Branch site | `192.168.40.0/24` | `Fa0/1–12` | |
| VLAN 50 | Branch site | `192.168.50.0/24` | `Fa0/13–24` | |

## Features Implemented

- **Inter-VLAN Routing** — Dallas router uses sub-interfaces (`g0/0.10`, `g0/0.20`, `g0/0.30`) as the gateway for each local VLAN.

- **DHCP Relay** — Austin-site VLANs receive DHCP addressing relayed from remote DHCP servers (Houston / Dallas) instead of a local DHCP server.

- **DNS Server** — Hosted in VLAN 30 at Dallas, resolving names such as `icca.com`.

- **Multi-site WAN** — Three routers interconnected over serial links forming a partial-mesh WAN.


## Project Files

| File | Description |
|---|---|
| `*.pkt` | Cisco Packet Tracer project file |
| `topology-diagram.png` | Topology screenshot |
| `README.md` | Project documentation |


## How to Use

- **Open the `.pkt` file** in Cisco Packet Tracer.
- **Review router sub-interface** and **DHCP relay (`ip helper-address`)** configurations.
- Use **Simulation mode** or **ping/PDUs** to verify connectivity across VLANs and between sites.

## References

- **Learned from the YouTube channel:** Channel Name

## Author

**Riya Patel**
- Learned from the YouTube channel: **The Last Hop Tech**
