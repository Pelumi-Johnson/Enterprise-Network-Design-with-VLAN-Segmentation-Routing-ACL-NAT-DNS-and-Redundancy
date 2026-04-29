# Enterprise Network Simulation with VLANs Routing ACL NAT DNS and Redundancy

## Overview
Designed and validated a complete enterprise network simulation integrating VLAN segmentation inter VLAN routing ACL based traffic control NAT for external access DNS for name resolution and Layer 2 redundancy. Captured full packet flow behavior using simulation recordings to demonstrate how traffic moves across the network under normal and controlled conditions.

## Objective
Built and validated a multi service network supporting departmental segmentation controlled communication external connectivity and fault tolerance while verifying behavior through real time packet flow simulation.

## Network Setup
Devices Used
1 Cisco 2960 Switch
1 Additional Switch for redundancy
2 Cisco 1941 Routers
1 Server
3 End Devices PCs
```
Topology Design
VLAN 10 HR uses subnet 192.168.10.0/24
VLAN 20 IT uses subnet 192.168.20.0/24
VLAN 30 Finance uses subnet 192.168.30.0/24
```

---

```
Switches connected using dual links to introduce redundancy
Router configured using Router on a Stick for inter VLAN routing
Edge router connected to ISP network for external access
Server configured on external network providing DNS and HTTP services
```
Logical Flow
PC to Access Switch to Distribution Router to Edge Router to Server and back

Full Topology and Packet Flow
![Full Simulation](https://github.com/Pelumi-Johnson/Enterprise-Network-Design-with-VLAN-Segmentation-Routing-ACL-NAT-DNS-and-Redundancy/blob/main/Top.gif)

---

## Configuration

### VLAN and Switching Configuration
Configured VLANs for HR IT and Finance and assigned access ports accordingly
Configured trunk link between switch and router
Configured redundant link between switches for failover testing

---

### Inter VLAN Routing
Configured subinterfaces with dot1Q encapsulation on router
Assigned gateway IPs for each VLAN

---

### ACL Configuration
Applied access control policies

- HR cannot access Finance
- Finance cannot access IT
- IT allowed full access

---

### NAT Configuration
Configured NAT overload to allow internal VLAN networks to access external network through a single public IP

---

### DNS and Server Configuration
- Configured DNS service on server
- Mapped domain name company.com to server IP
- Enabled HTTP service for testing browser access

---

## Validation

### DNS Request Simulation
Recorded packet flow showing DNS resolution process from client to server
```
Observation
Client sends DNS request
Server responds with resolved IP address
Traffic continues toward destination
```
DNS Request Flow
![DNS Flow](https://github.com/Pelumi-Johnson/Enterprise-Network-Design-with-VLAN-Segmentation-Routing-ACL-NAT-DNS-and-Redundancy/blob/main/DNS.gif)

---

### Access Control Validation
Recorded packet behavior under ACL enforcement

Observation
- HR traffic to Finance blocked
- Finance traffic to IT blocked
- IT traffic allowed across all VLANs

Video Placeholder ACL Behavior
![ACL Flow](https://github.com/Pelumi-Johnson/Enterprise-Network-Design-with-VLAN-Segmentation-Routing-ACL-NAT-DNS-and-Redundancy/blob/main/ACL%201.gif)
![ACL Flow](https://github.com/Pelumi-Johnson/Enterprise-Network-Design-with-VLAN-Segmentation-Routing-ACL-NAT-DNS-and-Redundancy/blob/main/ACL%202.gif)
![ACL Flow](https://github.com/Pelumi-Johnson/Enterprise-Network-Design-with-VLAN-Segmentation-Routing-ACL-NAT-DNS-and-Redundancy/blob/main/ACL%203.gif)

---

### End to End Communication
Recorded full packet traversal across VLAN routing NAT and external network
```
Observation
Traffic successfully routed translated and delivered to server
Return traffic correctly mapped back to originating host
```
Video Placeholder End to End Flow
![End to End Flow](./videos/end-to-end.mp4)

---

### Redundancy Validation
Simulated link failure between switches
```
Observation
Primary link removed
Backup link activated automatically
Traffic continued without disruption
```
Video Placeholder Redundancy Failover
![Redundancy Failover](./videos/redundancy.mp4)

---

## Key Concepts Applied
- Multi VLAN segmentation across departments
- Router on a Stick for inter VLAN communication
- ACL enforcement for traffic control
- NAT overload for external communication
- DNS resolution for domain access
- Layer 2 redundancy with failover validation
- End to end packet flow analysis using simulation mode

## Outcome
Successfully implemented a full enterprise style network simulation integrating segmentation routing security translation and redundancy. Verified that traffic followed the intended design under both normal and failure conditions. Demonstrated the ability to trace and explain complete network behavior from client request to server response.
