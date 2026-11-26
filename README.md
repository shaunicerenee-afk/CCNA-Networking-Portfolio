# CCNA-Networking-Portfolio
A collection of hands-on Cisco Packet Tracer projects demonstrating network design, routing, switching, VLANs, DHCP, and troubleshooting skills.
# CCNA Networking Portfolio

Welcome to my networking portfolio!

I am an aspiring IT networking professional currently studying for the Cisco Certified Network Associate (CCNA) certification. This repository showcases my hands-on experience with Cisco Packet Tracer, network configuration, troubleshooting, and network documentation.

## Technical Skills

- Cisco IOS CLI configuration
- IPv4 addressing and subnetting
- VLAN configuration and network segmentation
- IEEE 802.1Q trunking
- Inter-VLAN routing (Router-on-a-Stick)
- DHCPv4 configuration and address exclusions
- Static IPv4 addressing
- Spanning Tree Protocol (STP) and network redundancy
- Extended IPv4 ACL configuration and traffic filtering
- ICMP connectivity testing and ACL verification
- Network troubleshooting and documentation

## Networking Projects

### [Project 001: Small Office Network](Project-001-Small-Office-Network/)

**Platform:** Cisco Packet Tracer
**Status:** Completed

Designed and configured a small office network consisting of one Cisco router, one Cisco switch, four workstations, and two departmental VLANs.

**Key accomplishments:**
- Configured VLAN 10 (Administration) and VLAN 20 (Customer Support).
- Implemented router-on-a-stick inter-VLAN routing.
- Configured DHCPv4 pools for automatic IP address assignments.
- Verified same-VLAN connectivity, default gateway reachability, and inter-VLAN communication.
- Troubleshot and resolved a non-operational trunk connection.
- Documented network configurations and connectivity test results.

### [Project 002: Multi-Switch Network](Project-002-Multi-Switch-Network/)

**Platform:** Cisco Packet Tracer  
**Status:** Completed

Designed and configured a multi-switch office network consisting of three Cisco 2960 switches, one Cisco 2911 router, four workstations, and two departmental VLANs.

**Key accomplishments:**
- Configured VLANs across multiple Cisco switches.
- Implemented IEEE 802.1Q trunking between switches.
- Configured router-on-a-stick inter-VLAN routing.
- Configured DHCPv4 pools with excluded address ranges.
- Verified same-VLAN, gateway, and inter-VLAN connectivity.
- Independently diagnosed and resolved a router-to-switch connectivity issue.
- Documented network configurations and troubleshooting results.

### [Project 003: Redundant Switch Network & STP](Project-003-Redundant-Switch-Network/)

**Platform:** Cisco Packet Tracer  
**Status:** Completed

Designed and configured a redundant Layer 2 network using three Cisco 2960 switches, VLAN 10, and IEEE 802.1Q trunking. Configured a preferred STP root bridge and verified automatic failover during a simulated link failure.

**Key accomplishments:**
- Configured VLANs, access ports, and 802.1Q trunks.
- Configured S1 as the preferred root bridge for VLAN 10.
- Verified STP root, designated, and alternate port roles.
- Analyzed STP path costs and topology changes.
- Simulated a link failure and verified backup-path activation.
- Confirmed successful PC-to-PC connectivity during failover.
- Restored the original network topology and verified STP reconvergence.
  
### [Project 004: Secure Office Network & Extended ACLs](Project-004-Secure-Office-Network)

Platform: Cisco Packet Tracer  
Status: Completed

Designed and configured a secure office network using a Cisco 2911 router, a Cisco 2960 switch, four workstations, and an internal server. Implemented VLAN segmentation, router-on-a-stick inter-VLAN routing, DHCPv4, and an extended ACL to restrict guest access to employee resources.

Key accomplishments:
- Configured VLAN 10 (STAFF) and VLAN 20 (GUEST) with IEEE 802.1Q trunking.
- Implemented inter-VLAN routing using router subinterfaces.
- Configured DHCPv4 pools with excluded address ranges.
- Assigned a static IPv4 address to the internal server.
- Created and applied an extended named ACL to restrict guest access to the STAFF network.
- Verified security enforcement through connectivity testing and ACL match counters.
- Analyzed ICMP Request Timed Out and Destination Unreachable responses to understand ACL direction and return traffic.
- Documented network configurations, security testing, and troubleshooting results.
  
## Career Goals

My goal is to continue developing practical networking and troubleshooting skills while preparing for the CCNA certification and pursuing opportunities in IT networking and network administration.

This portfolio will be updated as I complete additional hands-on networking projects.
