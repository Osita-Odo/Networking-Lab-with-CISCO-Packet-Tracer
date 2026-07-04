# Cisco Packet Tracer: Networking Labs

**Network design, IP addressing, Cisco IOS configuration & troubleshooting**

## Objective

This project is a collection of hands-on networking labs built in Cisco Packet Tracer. Each lab walks through a core networking concept: from basic switching and connectivity testing, through router-based inter-network communication, DHCP and email services, all the way to VLAN segmentation. The screenshots document every step: the topology, the device configuration, and the verification (pings, show commands, and service tests) that proves it works. These labs were completed as practice in network design, IP addressing, Cisco IOS CLI configuration, and troubleshooting.

## Skills Learned

* Building logical network topologies in Cisco Packet Tracer.
* IP addressing and subnetting across multiple networks.
* Cisco IOS CLI configuration (hostnames, interfaces, `no shutdown`, IP assignment).
* Inter-network routing through a router.
* DHCP server setup and address-pool verification.
* Application-layer services: configuring an email (SMTP/POP3) server and clients.
* VLAN creation, naming, and access-port assignment for network segmentation.
* Verification and troubleshooting using `ping`, `show vlan`, `show ip dhcp pool`, and Simulation mode.

## Tools Used

* Cisco Packet Tracer (Logical and Simulation views).
* Cisco IOS command-line interface (CLI).
* Cisco devices: 2960-24TT switch, 2911 / ISR4331 routers, end devices (laptops, PCs), and a server.


---

## Lab 1: Basic LAN — Switch + Ping Connectivity

A simple local network: three end devices (two laptops and a PC) connected to a single 2960 switch, all on the `192.168.2.0/24` subnet.

### Topology
The base topology in Logical view. Laptop1 (`192.168.2.1`), Laptop0 (`192.168.2.2`), and PC2 (`192.168.2.3`) all connect to Switch0 (2960-24TT) with copper straight-through cabling. All link lights are green, meaning the physical and data-link layers are up.

<img width="900" height="594" alt="image" src="https://github.com/user-attachments/assets/ba544454-0493-4257-9eec-20bc21c3e874" />


*Screenshot 1: Base LAN topology*

### Simulation Mode
The same network running in Simulation mode. The Event List on the right logs each frame as it travels through the switch, and the bottom PDU panel shows two successful ICMP scenarios (Laptop1 to Laptop0, and PC2 to Laptop0). An envelope icon on the switch represents a packet in transit.

<img width="900" height="406" alt="image" src="https://github.com/user-attachments/assets/0bd858a9-b8eb-400a-8bd9-5059fda87bba" />


*Screenshot 2: Simulation mode with Event List*

### Ping Test from the Command Prompt
A `ping 192.168.2.2` followed by `ping 192.168.2.1`. Both return 4 replies, 0% loss with low round-trip times (~4–9 ms), confirming end-to-end Layer 3 reachability across the switch.

<img width="900" height="509" alt="image" src="https://github.com/user-attachments/assets/001098b8-1815-4ed0-8a0a-6da639b121f2" />


*Screenshot 3: Ping test results*

### Continuous Simulation
Simulation continuing to a later timestamp, with the Event List filling up as repeated ICMP traffic flows through Switch0. Interface labels (Fa0, Fa0/2) are now displayed on the links.

<img width="900" height="422" alt="image" src="https://github.com/user-attachments/assets/9e441c28-3c2f-48de-87be-484355fd51b7" />


*Screenshot 4: Continuous simulation*

### Ping Results Inside the Device Window
The same ping output viewed from inside the Desktop > Command Prompt tab of PC2. Both screenshots show the two successful ping batches (to .2.2 and .2.1) with 0% packet loss: the device-level proof that the LAN is fully connected.

<img width="900" height="380" alt="image" src="https://github.com/user-attachments/assets/f92e1046-ee86-4516-8139-79b7f77b2571" />


*Screenshot 6: Device-level ping (view 2)*

---

## Lab 2: Two-Network Communication Through a Router

This lab connects two separate networks (different IP schemes) so they can talk to each other through a router: the classic "router-between-networks" scenario.

### Router CLI Configuration
Router0 (Cisco 2911) being configured over the CLI. Key steps: `hostname R3`, then `interface g0/1` > `no shutdown` > `ip address 192.168.1.30 255.255.255.0`. The IOS messages confirm the interface and line protocol came up. The topology shows Network A (pink) with PC0 on VLAN 10 and PC1 on VLAN 20.

<img width="900" height="538" alt="image" src="https://github.com/user-attachments/assets/493fe764-592d-4250-be55-0e6bdc8fcf34" />


*Screenshot 7: Router CLI configuration*

### Cross-Network Ping Success
A `ping 192.168.1.40` from PC4 (VLAN 40 in Network B) returning 4 replies with 0% loss, confirming traffic successfully routes between the segments.

<img width="900" height="509" alt="image" src="https://github.com/user-attachments/assets/7913ec8b-a57b-415c-bb1a-c7f2378c5d39" />

*Screenshot 8: Cross-network ping success*

### Two-Network Topology with Addressing Labels
A clean diagram of the full design: NET A (green, 1.1.0.0 range) and NET B (orange, 10.10.0.0 range), each with its own switch and two PCs, joined by a central router. The label boxes document every device IP, default gateway, and subnet mask, plus the router interfaces (Gig0/1 and Gig0/2). It states the addressing plan and makes the gateway relationship between each LAN and the router explicit.


###<img width="600" height="300" alt="Annotated home-lab version of the two-network design" src="SCREENSHOT_13_URL" />

*Screenshot 13: Annotated home-lab version*

### Simulation of Inter-Network Traffic
The two-network design running in Simulation mode. The Event List records frames hopping across the switches, and the PDU panel shows successful ICMP between PCs on opposite networks (e.g. PC1 to PC4, PC3 to PC2).

<img width="600" height="300" alt="Inter-network simulation" src="SCREENSHOT_14_URL" />

*Screenshot 14: Inter-network simulation*

---

## Lab 3: DHCP Server Configuration

Here a router acts as a DHCP server, automatically handing out IP addresses to clients instead of configuring each one by hand.

### Router DHCP Pool Configuration
The router CLI showing the DHCP setup: `ip dhcp excluded-address 192.168.1.1` (reserve the gateway), `ip dhcp pool office`, `network 192.168.1.0 255.255.255.0`, `default-router 192.168.1.1`, and `dns-server 8.8.8.8`. The `show ip dhcp pool` output confirms the office pool: 254 total addresses, range 192.168.1.1 – 192.168.1.254. The screenshots also capture the common `dns server` vs `dns-server` syntax slip and its correction.

<img width="600" height="300" alt="DHCP pool configuration" src="SCREENSHOT_9_URL" />

*Screenshot 9: DHCP pool configuration*

<img width="600" height="300" alt="show ip dhcp pool verification" src="SCREENSHOT_39_URL" />

*Screenshot 39: show ip dhcp pool verification*

### Client IP Configuration
PC0 IP Configuration window showing the addressing the DHCP pool serves (`192.168.1.x` / `255.255.255.0`, gateway `192.168.1.1`, DNS `8.8.8.8`): useful for comparing manual vs automatic assignment.

<img width="600" height="300" alt="Client IP configuration" src="SCREENSHOT_10_URL" />

*Screenshot 10: Client IP configuration*

### Verifying Client Connectivity
From PC2, pinging `192.168.1.3` and `192.168.1.4` (other clients that pulled addresses from the pool). Both succeed with 0% loss, proving the DHCP-assigned hosts can reach each other.

<img width="600" height="300" alt="Client connectivity test" src="SCREENSHOT_11_URL" />

*Screenshot 11: Client connectivity test*

### Full DHCP Lab Side by Side
The complete workspace: topology (router > switch > office LAN of PC0/PC1/PC2 plus a server), the router DHCP configuration and `show ip dhcp pool` output, and a client IP Configuration panel: all visible together.

<img width="600" height="300" alt="Router DHCP detail, full workspace" src="SCREENSHOT_38_URL" />

*Screenshot 38: Router DHCP detail*

---

## Lab 4: Email Server & Mail Client Configuration

This lab stands up an email service on a server and configures clients to send and receive mail through it. The underlying network has the clients (Laptop0, Laptop1, PC2) on `192.168.2.0` and the Email Server on `192.168.3.0`, joined by a router.

### Router Setup for the Mail Network
Router0 configured to connect the two subnets. Steps: `hostname R1`, `interface g0/0` > `no shutdown`, then assigning addresses. These screenshots also capture a useful troubleshooting moment: the IOS error "Bad mask /24 for address 192.168.2.0", a reminder that 192.168.2.0 is the network address and the interface needs a usable host address. Configuration continues on g0/1 with `192.168.3.2 255.255.255.0` for the server side.

<img width="600" height="300" alt="Router setup for the mail network, view 1" src="SCREENSHOT_15_URL" />

*Screenshot 15: Router setup (view 1)*

<img width="600" height="300" alt="Bad mask troubleshooting error" src="SCREENSHOT_16_URL" />

*Screenshot 16: Bad mask troubleshooting*

<img width="600" height="300" alt="Router setup continued" src="SCREENSHOT_17_URL" />

*Screenshot 17: Router setup continued*

### Server EMAIL Service Setup
Server0 > Services > EMAIL. The domain is set to google.com, and a user account (ORGSec) is created with a password. This turns the server into the SMTP/POP3 mail host for the domain.

<img width="600" height="300" alt="EMAIL service setup view 1" src="SCREENSHOT_18_URL" />

*Screenshot 18: EMAIL service (view 1)*

<img width="600" height="300" alt="EMAIL service setup view 2" src="SCREENSHOT_19_URL" />

*Screenshot 19: EMAIL service (view 2)*

### Adding More Mail Users
The EMAIL service with the domain changed to google.org and additional user accounts (osita, meet) added to the user list.

<img width="600" height="300" alt="Adding mail users" src="SCREENSHOT_20_URL" />

*Screenshot 20: Adding mail users*

### Configuring the Mail Client
The Desktop > Configure Mail wizard on the laptops. Each client gets a display name, an email address (e.g. osita@google.com, meet@google.com), incoming/outgoing mail servers pointing at `192.168.3.1`, and logon credentials.

<img width="600" height="300" alt="Configure Mail wizard view 1" src="SCREENSHOT_21_URL" />

*Screenshot 21: Configure Mail (view 1)*

<img width="600" height="300" alt="Configure Mail wizard view 2" src="SCREENSHOT_22_URL" />

*Screenshot 22: Configure Mail (view 2)*

### Sending Mail
The Mail Browser on Laptop1. The status bar confirms "Sending mail to OrgSec@google.com … Send Success." The PDU panel records the SMTP exchange as successful, proving the mail flow works between clients via the server.

<img width="600" height="300" alt="Send mail success view 1" src="SCREENSHOT_23_URL" />

*Screenshot 23: Send mail success (view 1)*

<img width="600" height="300" alt="Send mail success view 2" src="SCREENSHOT_24_URL" />

*Screenshot 24: Send mail success (view 2)*

---

## Lab 5: VLAN Configuration

The final lab segments one physical switch into three logical networks (VLANs) for different departments, then connects them up to a router.

### Creating VLANs and Assigning Ports
The switch CLI (S1) showing the core VLAN workflow: `vlan 10` > `name IT`, `vlan 20` > `name HR`, `vlan 30` > `name Sales`, then `interface range fa0/1-3` > `switchport mode access` > `switchport access vlan 10` (and the equivalent ranges for HR and Sales). The `show vlan brief` output confirms the three VLANs are active with the correct ports assigned. The screenshots also capture the learning moments: e.g. `name IT Department` being rejected because of the space, and `switchmode` vs `switchport mode`.

<img width="600" height="300" alt="Creating VLANs on the switch CLI" src="SCREENSHOT_25_URL" />

*Screenshot 25: Creating VLANs*

<img width="600" height="300" alt="Assigning ports to VLANs" src="SCREENSHOT_28_URL" />

*Screenshot 28: Assigning ports to VLANs*

<img width="600" height="300" alt="show vlan brief output" src="SCREENSHOT_29_URL" />

*Screenshot 29: show vlan brief*

### VLAN Topology + Verification
The topology with the three color-coded department VLANs (IT = green, HR = blue, Sales = orange) hanging off one switch, shown alongside the `show vlan` output that verifies the port-to-VLAN mapping.

<img width="600" height="300" alt="VLAN topology and verification view 1" src="SCREENSHOT_26_URL" />

*Screenshot 26: VLAN topology + verify (view 1)*

<img width="600" height="300" alt="VLAN topology and verification view 2" src="SCREENSHOT_27_URL" />

*Screenshot 27: VLAN topology + verify (view 2)*

<img width="600" height="300" alt="VLAN topology and verification view 3" src="SCREENSHOT_30_URL" />

*Screenshot 30: VLAN topology + verify (view 3)*

### Router Configuration for the VLANs
Router0 (ISR4331) configured to provide connectivity: `hostname R1`, `interface g0/0/0` > `no shutdown` > `ip address 192.168.2.2 255.255.255.0`, plus a second interface (g0/0/1). The IOS log shows interfaces transitioning up and down, which is normal as links are attached.

<img width="600" height="300" alt="Router config for VLANs view 1" src="SCREENSHOT_31_URL" />

*Screenshot 31: Router config (view 1)*

<img width="600" height="300" alt="Router config for VLANs view 2" src="SCREENSHOT_33_URL" />

*Screenshot 33: Router config (view 2)*

<img width="600" height="300" alt="Router config for VLANs view 3" src="SCREENSHOT_34_URL" />

*Screenshot 34: Router config (view 3)*

<img width="600" height="300" alt="Router config for VLANs view 4" src="SCREENSHOT_36_URL" />

*Screenshot 36: Router config (view 4)*

### VLAN Client IP Configuration
PC12 IP Configuration: static `192.168.1.10` / `255.255.255.0`, gateway `192.168.2.2`: placing it in the IT VLAN and pointing it at the router.

<img width="600" height="300" alt="VLAN client IP configuration" src="SCREENSHOT_32_URL" />

*Screenshot 32: VLAN client IP configuration*

### Final VLAN Topology
The finished design: the router connects via Gig0/0/0 (`192.168.2.2`) and trunk Fa0/10 down to the switch, which fans out to the three department VLANs with their subnets (`192.168.x.10/.20/.30`).

<img width="600" height="300" alt="Final VLAN topology" src="SCREENSHOT_35_URL" />

*Screenshot 35: Final VLAN topology*

---

## Conclusion

Together these labs cover the everyday building blocks of a small network: connecting hosts through a switch, routing between separate networks, automating addressing with DHCP, running an application service (email), and segmenting a switch with VLANs. Each lab follows the same disciplined pattern: design the topology, configure the devices, then verify, which is exactly the workflow used when standing up real infrastructure. The result is a practical, end-to-end demonstration of foundational networking and Cisco IOS configuration skills.

---

> **How to attach the screenshots:** each image slot above uses a placeholder in its `src` (for example `SCREENSHOT_1_URL`). Upload each screenshot to this GitHub repository (drag-and-drop into the README editor, or add them to a `/screenshots` folder), then replace each `SCREENSHOT_X_URL` with the generated link. The numbering matches the original lab screenshot numbers, so `SCREENSHOT_39_URL` takes the image labelled "Screenshot 39", and so on.
