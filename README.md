# Network Infrastructure

## Purpose

Securing a network starts with understanding how it is built. These labs develop that foundation: how devices connect, how traffic moves between networks, how addresses are assigned, and how VLANs separate users into controlled segments. Every lab follows the same workflow used on real infrastructure: design the topology, configure the devices, then verify that it works. This groundwork supports later security tasks such as reading packet captures, spotting misconfigurations and planning segmentation.

## Labs Completed

| Project | Lab | Objective | Tools used | Lessons learnt |
|---|---|---|---|---|
| [Cisco Packet Tracer: Networking Labs](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer)<br>*Platform: Cisco Packet Tracer* | [Basic LAN: Switch and Ping Connectivity](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer#lab-1-basic-lan--switch--ping-connectivity) | Connect three hosts through a switch and confirm they can reach each other. | Catalyst 2960 switch, `ping`, Simulation mode | Green link lights show a cable is connected; only a successful ping proves hosts can communicate. |
| | [Two-Network Communication Through a Router](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer#lab-2-two-network-communication-through-a-router) | Route traffic between two separate networks. | Cisco 2911 router, IOS CLI (`hostname`, `ip address`, `no shutdown`) | Hosts on different networks need the router interface as their default gateway. |
| | [DHCP Server Configuration](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer#lab-3-dhcp-server-configuration) | Configure a router to assign IP addresses to clients automatically. | IOS CLI (`ip dhcp pool`, `ip dhcp excluded-address`), `show ip dhcp pool` | Reserve the gateway address first, and type commands exactly (`dns-server`, not `dns server`). |
| | [Email Server and Mail Client Configuration](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer#lab-4-email-server--mail-client-configuration) | Set up a mail server and clients to send mail across two subnets. | Server EMAIL service, mail client, SMTP/POP3, router CLI | An interface needs a usable host address, not the network address. |
| | [VLAN Configuration](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer#lab-5-vlan-configuration) | Segment one switch into IT, HR and Sales VLANs. | IOS CLI (`vlan`, `switchport access vlan`), `show vlan brief`, ISR4331 router | VLANs separate departments on one switch, and VLAN names cannot contain spaces. |
| [Building a Network from a Network Diagram](https://github.com/Osita-Odo/Networking-Lab-with-CISCO-Packet-Tracer)<br>*Platform: Cisco Packet Tracer (Physical Mode)* | Building a Network from a Network Diagram | Turn a logical diagram into a connection table and a fully cabled physical build. | Cisco 4321 routers, Catalyst 2960 switches, straight-through cabling | Documenting every connection first made the build fast and error-free. |
