# Project 003: Redundant Switch Network & Spanning Tree Protocol

## Project Overview
Designed and configured a redundant Layer 2 network using three Cisco 2960 switches and two workstations in Cisco Packet Tracer. Implemented VLAN segmentation, IEEE 802.1Q trunking, and Per-VLAN Spanning Tree Plus (PVST+) to prevent Layer 2 loops and provide alternate connectivity during a link failure.

## Network Topology
![Network Topology](network-topology.png)

### Network Devices
- 3 Cisco 2960 switches (S1, S2, S3)
- 2 PCs (PC0, PC1)
- Redundant triangle topology with three switch-to-switch connections

### Physical Connections
| Source | Interface | Destination | Interface |
|---|---|---|---|
| S1 | Fa0/1 | S2 | Fa0/1 |
| S1 | Fa0/2 | S3 | Fa0/1 |
| S2 | Fa0/2 | S3 | Fa0/2 |
| S2 | Fa0/3 | PC0 | Fa0 |
| S3 | Fa0/3 | PC1 | Fa0 |

## VLAN and IP Addressing
| Device | Interface | VLAN | IPv4 Address | Subnet Mask |
|---|---|---|---|---|
| PC0 | S2 Fa0/3 | 10 | 192.168.10.11 | 255.255.255.0 |
| PC1 | S3 Fa0/3 | 10 | 192.168.10.12 | 255.255.255.0 |

- VLAN 10 name: ADMINISTRATION
- Subnet: 192.168.10.0/24
- Addressing method: Static IPv4
- Default gateway: Not required for same-subnet communication

## Switch Configuration

### VLAN Configuration (S1, S2, S3)
```cisco
configure terminal
vlan 10
 name ADMINISTRATION
end
```

### Trunk Configuration (S1, S2, S3)
```cisco
configure terminal
interface range fa0/1-2
 switchport mode trunk
end
```

### Access Port Configuration
On S2 and S3:
```cisco
configure terminal
interface fa0/3
 switchport mode access
 switchport access vlan 10
end
```

### Root Bridge Configuration (S1)
```cisco
configure terminal
spanning-tree vlan 10 priority 4096
end
```

Configured S1 as the preferred root bridge for VLAN 10. The displayed Bridge ID priority became 4106 (base priority 4096 plus VLAN ID 10).

## STP Verification
Used `show spanning-tree vlan 10` to verify the root bridge, path costs, and port roles after convergence.

| Switch | Interface | Port Role | State |
|---|---|---|---|
| S1 | Fa0/1 | Designated | Forwarding |
| S1 | Fa0/2 | Designated | Forwarding |
| S2 | Fa0/1 | Root | Forwarding |
| S2 | Fa0/2 | Designated | Forwarding |
| S3 | Fa0/1 | Root | Forwarding |
| S3 | Fa0/2 | Alternate | Blocking |

S1 successfully became the root bridge for VLAN 10. STP blocked S3 Fa0/2 to prevent a Layer 2 switching loop while retaining a redundant path.

## Link Failure and Recovery Testing

### Failure Simulation
Administratively disabled S3 Fa0/1, the direct connection from S3 to S1:
```cisco
configure terminal
interface fa0/1
 shutdown
end
```

Observed the following changes:
- S3 Fa0/2 changed from Alternate/Blocking to Root/Forwarding.
- S3's root path cost increased from 19 to 38.
- Traffic could reach S1 through the alternate path via S2.
- PC0 successfully pinged PC1 at `192.168.10.12` after convergence.

### Recovery Simulation
Restored the original link:
```cisco
configure terminal
interface fa0/1
 no shutdown
end
```

After reconvergence:
- S3 Fa0/1 returned to Root/Forwarding.
- S3 Fa0/2 returned to Alternate/Blocking.
- Root path cost returned from 38 to 19.

**Result:** Successfully validated STP failover, backup-path activation, and restoration of the original forwarding topology.

## Verification Commands
```cisco
show vlan brief
show interfaces trunk
show spanning-tree vlan 10
show running-config
```

## Skills Demonstrated
- VLAN creation and access port configuration
- IEEE 802.1Q trunk configuration and verification
- STP/PVST+ root bridge election and priority configuration
- Root, designated, and alternate port identification
- Spanning-tree path cost interpretation
- Layer 2 redundancy and failover testing
- Switch CLI verification and network troubleshooting
- Technical documentation using Cisco Packet Tracer and GitHub

## Project Files
- `Project_003_Redundant_Switch_Network.pkt` - Cisco Packet Tracer project file
- `network-topology.png` - Network diagram with configuration and testing notes

## Project Status
**Completed:** Network configuration, connectivity verification, STP failover, and recovery testing.
