# LAB 1 - Basic DHCP Assignment & Connectivity Verification

**Objective**  
Build a simple LAN using GNS3, configure VyOS as a DHCP server, dynamically assign IPs to VPCS nodes from a defined range, verify Layer 3 connectivity with ping, and analyze traffic using Wireshark.

**Tools**  
- GNS3 2.2.54 + GNS3 VM (VMware)  
- VyOS 1.4 rolling  
- VPCS (Virtual PC Simulator)  
- Wireshark

## Topology
[screenshots/Topology.png]

## Configuration Highlights
### VyOS DHCP Server (exact config used)
```bash
set interfaces ethernet eth0 address 192.168.1.1/24
set service dhcp-server shared-network-name LAN subnet 192.168.1.0/24 start 192.168.1.100 stop 192.168.1.200
set service dhcp-server shared-network-name LAN subnet 192.168.1.0/24 default-router 192.168.1.1
set service dhcp-server shared-network-name LAN subnet 192.168.1.0/24 dns-server 8.8.8.8
commit ; save
