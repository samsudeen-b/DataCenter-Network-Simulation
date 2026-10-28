# Data Center Network Simulation & Troubleshooting Lab

## Overview
A simulated data center network built using Cisco Packet Tracer to practice network deployment, VLAN segmentation, inter-VLAN routing, connectivity validation, and troubleshooting.

## Network Architecture
- 1 Cisco 1941 router
- 3 Cisco 2960 switches
- 4 simulated servers
- 1 administrator workstation

## Technologies
Cisco Packet Tracer, TCP/IP, VLANs, 802.1Q trunking, static IPv4 addressing, router-on-a-stick routing, and ICMP diagnostics.

## Network Segmentation
| VLAN | Purpose | Subnet |
|---|---|---|
| 10 | Application | 192.168.10.0/24 |
| 20 | Management | 192.168.20.0/24 |
| 30 | Administration | 192.168.30.0/24 |

## Validation
Successfully completed eight connectivity tests covering gateway access and communication between the administrator workstation and servers across VLANs.

## Troubleshooting Exercises
- Simulated incorrect server IP addressing and restored connectivity.
- Simulated incorrect switch-port VLAN assignment and restored the intended configuration.
- Planned: Physical cable disconnection and recovery exercise.

## Limitations
This project uses simulated Cisco devices and does not represent production data center deployment or physical hardware maintenance experience.