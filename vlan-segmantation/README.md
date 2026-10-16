# Small Business Network — VLAN Segmentation

## 1. Project Overview

**Project type:** Network Simulation  
**Tool:** Cisco Packet Tracer  
**Difficulty:** Beginner  
**Status:** In Progress

### Objective

The objective of this project is to design and simulate a small-business network using Virtual Local Area Networks (VLANs) to separate the Sales and IT departments.

This project demonstrates basic switch configuration, VLAN segmentation, IPv4 addressing, and network connectivity testing.

## 2. Network Requirements

- Create two separate VLANs: Sales and IT.
- Assign the correct switch ports to each VLAN.
- Configure IPv4 addresses on all PCs.
- Verify VLAN membership and network connectivity.
- Document configuration steps and test results.

## 3. Network Topology

<img width="632" height="413" alt="image" src="https://github.com/user-attachments/assets/69524974-ceb3-4e72-b957-8646d67b7316" />


**Topology description:**  
The network consists of one managed switch, a router and four PCs. Two PCs belong to Sales (VLAN 10), while the other two belong to IT (VLAN 20).

## 4. IP Addressing Plan

| Device | VLAN | IP Address | Subnet Mask |

| PC1 | Sales (10) | 192.168.10.11 | 255.255.255.0 |
| PC2 | Sales (10) | 192.168.10.12 | 255.255.255.0 |
| PC3 | IT (20) | 192.168.20.11 | 255.255.255.0 |
| PC4 | IT (20) | 192.168.20.12 | 255.255.255.0 |

Default gateways are not configured because this initial lab does not include a router.

## 5. Configuration

### VLAN Creation

SW1(config)#interface range interface
SW1(config-if)#switchport mode access
SW1(config-if)#switchport access vlan 10

### Switch Port Assignment
<img width="725" height="244" alt="image" src="https://github.com/user-attachments/assets/a0d3e208-9188-44c5-a071-fcfcbc982841" />

## 6. Testing and Results

| Test | Expected Result | Actual Result |
|---|---|---|
| PC1 to PC2 ping | Success | Pending |
| PC3 to PC4 ping | Success | Pending |
| PC1 to PC3 ping | Failure | Pending |


PC1 pings PC2 : Success
<img width="532" height="341" alt="image" src="https://github.com/user-attachments/assets/472c4330-25a2-4011-b16a-285126c01b62" />

PC3 Pings PC4 : Success
<img width="544" height="377" alt="image" src="https://github.com/user-attachments/assets/555e8944-0723-4dc8-96c7-ad8fc598c4b9" />

PC1 pings PC3 : Failure
<img width="569" height="315" alt="image" src="https://github.com/user-attachments/assets/97eea779-e165-4c13-99e6-b7bc8232181c" />

## 7. Troubleshooting

**Problem encountered:**  
[PC1 cannot ping PC 3]

**Diagnosis:**  
[PC1 fails to send traffic to PC3 as it is outside its network and there is no router to send the default gateway]

**Solution:**  
[1. Added ROAS(Router On A Stick) and configure ip address of 192.168.20.254/30 on interface g0/0]
[2. Configured the defult gateway for each PCs]
[3. VLAN 10 and VLAN 20 can now communicate through the default gateway]
[4. PC1 can now ping PC2]
<img width="536" height="345" alt="image" src="https://github.com/user-attachments/assets/bc06c4b3-91b5-430c-a085-f26baa4ad486" />


## 8. Key Learnings

- Learned how to create and name VLANs.
- Learned how to assign switch access ports to VLANs.
- Learned how VLANs separate Layer 2 broadcast domains.
- Practised verifying configurations and testing connectivity.
- Learned how to create ROAS(Router On A Stick) to connect different VLANs

## 9. Project Files

- `vlan-segmentation.pkt` — Packet Tracer simulation.
- `screenshots/` — topology, configuration and test evidence.
