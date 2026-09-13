


![topology-diagram05](topology-diagram05.png)



Site-to-Site IPSec VPN

A Cisco Packet Tracer project demonstrating a Site-to-Site IPSec VPN tunnel between an HQ site and a Branch site, secured through Cisco ASA 5506-X firewalls across an ISP router.




Topology Overview

## Network Topology

### HQ Site — Pink (`192.168.10.0/24`)
- **Switch (2960-24TT)**
  - Connects PC0 and PC1
  - Uplink to Router1 (`Gig0/1`)

- **Router1 — HQ Edge Router (2911)**
  - `Gig0/0` → ASA0 (`Gig1/2`) — `10.10.10.0/30`
  - `Gig0/1` → HQ LAN Switch

- **ASA0 — HQ Firewall (5506-X)**
  - `Gig1/2` → Router1
  - `Gig1/1` → ISP Router (`Gig0/0`) — `100.50.10.0/30`

- **ISP Router**
  - `Gig0/0` → ASA0 — `100.50.10.0/30`
  - `Gig0/1` → ASA1 — `100.50.10.4/30`
  - Sits between the two ASA firewalls

- **ASA1 — Branch Firewall (5506-X)**
  - `Gig1/1` → ISP Router
  - `Gig1/2` → Router2 — `10.10.10.4/30`

- **Router2 — Branch Edge Router**
  - `Gig0/1` → ASA1
  - `Gig0/0` → Branch LAN Switch

### Branch Site — Blue (`192.168.20.0/24`)
- **Switch (2960-24TT)**
  - Connects PC2 and PC3
  - Uplink to Router2



## IP Addressing

| Link | Subnet |
|---|---|
| Router1 ↔ ASA0 | `10.10.10.0/30` |
| ASA0 ↔ ISP Router | `100.50.10.0/30` |
| ISP Router ↔ ASA1 | `100.50.10.4/30` |
| ASA1 ↔ Router2 | `10.10.10.4/30` |
| HQ LAN | `192.168.10.0/24` |
| Branch LAN | `192.168.20.0/24` |


Features Implemented
Site-to-Site IPSec VPN — configured between ASA0 (HQ) and ASA1 (Branch) to securely tunnel traffic between the HQ and Branch LANs over the ISP transit network.

ASA Firewalls — each site is protected by a Cisco ASA 5506-X sitting between the internal edge router and the public/ISP-facing link.

ISP Simulation — a router in the middle represents the public internet/ISP path the VPN tunnel traverses.



Files


## Project Files

| File | Description |
|---|---|
| `*.pkt` | Cisco Packet Tracer project file |
| `topology-diagram.png` | Topology screenshot |
| `README.md` | Project documentation and configuration details |


How to Use


Open the .pkt file in Cisco Packet Tracer.
Review the ASA IPSec VPN configuration (ISAKMP/IKE Phase 1, IPSec Phase 2, crypto maps, ACLs matching interesting traffic).
Ping between PC0/PC1 (HQ) and PC2/PC3 (Branch) to verify the VPN tunnel is passing traffic, and check ASA VPN status to confirm the tunnel is up.

References
Learned from the YouTube channel: RM TECH NETWORK 
Author

Riya Patel
