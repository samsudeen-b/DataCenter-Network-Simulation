# Data Center Network Troubleshooting Report

## Project Overview

**Project:** Data Center Network Simulation & Troubleshooting Lab  
**Platform:** Cisco Packet Tracer  
**Network Devices:** 1 router, 3 switches, 4 servers, 1 administrator PC

**Objective:** Simulate common network failures, identify their root causes, restore connectivity, and document troubleshooting procedures.

## Network Configuration

| VLAN | Purpose | Subnet | Gateway |
|---|---|---|---|
| 10 | Application Servers | 192.168.10.0/24 | 192.168.10.1 |
| 20 | Management Servers | 192.168.20.0/24 | 192.168.20.1 |
| 30 | Administration | 192.168.30.0/24 | 192.168.30.1 |

## Incident 001 — Incorrect Server IP Address

**Affected Device:** Server2  
**Expected IP:** 192.168.10.10  
**Incorrect IP:** 192.168.50.10  
**Severity:** Simulated connectivity failure

### Problem

Server2 was intentionally assigned an incorrect IPv4 address outside its designated VLAN 10 subnet.

### Diagnosis

1. Changed Server2's IP address to 192.168.50.10.
2. Executed `ping 192.168.10.10` from PC1.
3. Observed 100% packet loss.
4. Inspected Server2's IP configuration and identified the incorrect address.

### Resolution

Restored Server2's IP address to 192.168.10.10 while retaining the subnet mask 255.255.255.0 and gateway 192.168.10.1.

### Outcome

The original IP addressing fault was corrected, and the network was returned to its intended configuration.

## Incident 002 — Incorrect VLAN Assignment

**Affected Device:** Server2  
**Switch:** APP-SW  
**Port:** FastEthernet0/2  
**Correct VLAN:** 10  
**Incorrect VLAN:** 20

### Problem

Server2's switch port was deliberately moved from VLAN 10 to VLAN 20 while its IP address remained unchanged.

### Diagnosis

1. Changed APP-SW FastEthernet0/2 to VLAN 20.
2. Executed `show vlan brief`.
3. Confirmed that Fa0/2 appeared under VLAN 20 instead of VLAN 10.
4. Identified the incorrect switch-port VLAN assignment as the fault.

### Resolution

Restored the correct VLAN using:

```bash
configure terminal
interface fastEthernet 0/2
switchport access vlan 10
end
write memory
```

### Outcome

The switch-port assignment was restored to VLAN 10, returning the network to its intended configuration.

## Connectivity Validation

Eight connectivity tests were reported successful, including:

- Server3 to VLAN 10 gateway
- Server4 and Server5 to VLAN 20 gateway
- PC1 to VLAN 30 gateway
- PC1 to Server2, Server3, Server4 and Server5

## Skills Demonstrated

- Cisco IOS CLI configuration
- IPv4 addressing and subnetting
- VLAN configuration and verification
- 802.1Q trunking
- Router-on-a-stick inter-VLAN routing
- ICMP connectivity testing
- Network fault simulation and troubleshooting
- Technical incident documentation

## Future Experiment

**Incident 003 — Physical Cable Disconnection**

Planned exercise: Simulate a disconnected Ethernet cable, identify the affected interface, reconnect the cable and verify service restoration.

## Lab Limitations

All experiments were conducted using Cisco Packet Tracer. The project demonstrates simulated networking and troubleshooting, not production data center operations or physical hardware replacement.