# Change Ticket NET-2025-002 – VLAN Segmentation & Inter-VLAN Routing

**Date:** 09 December 2025  
**Environment:** GNS3 2.2.54 – VyOS 1.5 – VPCS  
**Change Type:** Planned Network Segmentation  

### Business Request
Implement VLANs to separate Sales and IT departments for security and performance.

### Implementation Steps
1. Created VLAN 10 (Sales) and VLAN 20 (IT)
2. Configured 802.1Q trunk between switch and VyOS router
3. Built router-on-a-stick topology:
   - `set interfaces ethernet eth0 vif 10 address 192.168.10.1/24`
   - `set interfaces ethernet eth0 vif 10 description "Sales VLAN"`
   - `set interfaces ethernet eth0 vif 20 address 192.168.20.1/24`
   - `set interfaces ethernet eth0 vif 20 description "IT VLAN"`
4. Assigned client PCs to correct VLANs via VPCS `vlan` command
5. Committed and saved configuration

### Verification Performed
- Intra-VLAN connectivity within VLAN 10 and VLAN 20: SUCCESS
- Inter-VLAN routing (Sales ↔ IT): SUCCESS  
- 802.1Q tagging confirmed in Wireshark capture  

### Rollback Plan
`delete interfaces ethernet eth0 vif 10`  
`delete interfaces ethernet eth0 vif 20`  
`commit && save`

### Result
Change completed successfully. Sales and IT are now segmented with full inter-VLAN communication.

**Time to Complete:** 35 minutes  
**Status:** CLOSED – SUCCESSFUL

---
*Part of Network+ Home Lab Series – Lab 2*
