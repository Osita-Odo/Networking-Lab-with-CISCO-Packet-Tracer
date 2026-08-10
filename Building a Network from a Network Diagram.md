# Building a Network from a Network Diagram

**Cisco Packet Tracer · Physical Mode 

**Focus areas:** Network fundamentals, structured cabling, network documentation

---

## Overview

This lab exercise involved constructing a small enterprise network in Cisco Packet Tracer, working from a supplied logical network diagram through to a fully cabled physical build. The goal was to int[...]

Network diagrams are the reference point technicians rely on when planning, troubleshooting, and maintaining infrastructure. This exercise demonstrates the core workflow of moving from a design on pap[...]

## Objectives

- Interpret a logical network diagram and identify how each device connects.
- Produce accurate connection documentation in a device table.
- Select the correct cabling and build the physical topology in Packet Tracer's Physical Mode.
- Verify connectivity and confirm the build against the design.

## Lab Environment

| | |
|---|---|
| **Platform** | Cisco Packet Tracer (Logical and Physical Mode) |
| **Devices** | 2 × Cisco 4321 routers (R1, R2), 2 × Catalyst 2960 switches (S1, S2), 1 web server, 2 PCs (PC-A, PC-B) |
| **Cabling** | Copper straight-through Ethernet throughout |

## The Network Design

The logical diagram defines the intended topology. R1 anchors one side of the network with a directly attached web server, while R2 sits behind S2 on the other side. The two switches are trunked toget[...]

<img width="863" height="505" alt="image" src="https://github.com/user-attachments/assets/53791f42-6510-4219-bbf8-fe32e5808de4" />


*Figure 1 — Logical network diagram provided for the build.*

## Part 1 — Documenting the Connections

Before touching any cabling, I worked through the diagram interface by interface and recorded every connection in the device table below. This documentation step is deliberately done first: it removes[...]

| Device Name | Device Type | Local Interface | Connected Device & Port |
|---|---|---|---|
| R1 | Router / Cisco 4321 | G0/0/0 | Web Server, Ethernet0 |
| R1 | Router / Cisco 4321 | G0/0/1 | S1, G0/1 |
| S1 | Switch / Catalyst 2960 | G0/1 | R1, G0/0/1 |
| S1 | Switch / Catalyst 2960 | G0/2 | S2, G0/2 |
| S1 | Switch / Catalyst 2960 | F0/1 | PC-A, Ethernet0 |
| S2 | Switch / Catalyst 2960 | G0/1 | R2, G0/0/1 |
| S2 | Switch / Catalyst 2960 | G0/2 | S1, G0/2 |
| S2 | Switch / Catalyst 2960 | F0/1 | PC-B, Ethernet0 |
| R2 | Router / Cisco 4321 | G0/0/1 | S2, G0/1 |
| Web Server | Server | Ethernet0 | R1, G0/0/0 |
| PC-A | PC | Ethernet0 | S1, F0/1 |
| PC-B | PC | Ethernet0 | S2, F0/1 |

## Part 2 — Building the Physical Topology

### Step 1 — Selecting the cable type

From the diagram, all links are Ethernet, so the build uses copper straight-through cabling. On the cable pegboard in the main wiring closet, the straight-through cables are the green ones, confirmed [...]

> **Question:** What colour are the straight-through Ethernet cables in Packet Tracer?
> **Answer:** Green.

### Step 2 — Connecting the devices

Working in Physical Mode, I mounted the routers, switches, and web server in the equipment rack and cabled each link according to the connection table. As an example, to connect R1 to the web server I[...]

<img width="1920" height="1080" alt="Screenshot 2026-08-10 223332" src="https://github.com/user-attachments/assets/ac469e39-c1d4-4de1-bd03-c34d67b8f730" />


*Figure 2 — Equipment rack cabled in Physical Mode, with the straight-through cable highlighted on the pegboard.*

<img width="1920" height="1080" alt="Screenshot 2026-08-10 223123" src="https://github.com/user-attachments/assets/3339d023-eda1-4c46-95e5-8f9ba66a53c4" />


*Figure 3 — PC-A and PC-B cabled at the workbench, completing the end-device connections.*

## Verification & Result

<img width="1920" height="1080" alt="Screenshot 2026-08-10 222931" src="https://github.com/user-attachments/assets/3b5ae5ad-00b6-485a-85c7-7a8f83e736e2" />


Two checks confirmed the build was correct. First, every port LED across the routers, switches, server, and PCs showed a steady link state after cabling. Second, Packet Tracer's built-in completion ch[...]

- All device interfaces connected as documented in the connection table.
- Correct copper straight-through cabling used on every link.
- Port LEDs confirmed active links across all devices.
- Packet Tracer completion score: 100%.

## Skills Demonstrated

| Skill | Demonstrated Through |
|---|---|
| Physical topology build | Assembled a rack-based physical topology in Packet Tracer's Physical Mode from a logical diagram. |
| Interface mapping | Translated a logical diagram into an accurate device/interface connection table. |
| Cabling | Selected the correct copper straight-through cabling for router, switch, server, and end-device links. |
| Structured cabling concepts | Worked with racks, patch panels, and a wiring-closet layout that mirrors real deployments. |
| Verification | Confirmed link status via port LED indicators and Packet Tracer's completion checker (100%). |
| Documentation | Produced clear network documentation suitable for troubleshooting and handover. |

## Reflection

The most valuable part of this exercise was the discipline of documenting every connection before building anything. Mapping the logical diagram to a precise device table made the physical build fast and error-free, and it produced documentation that would be immediately useful to anyone maintaining the network later. The distinction between logical and physical views, one showing how data flows, the other showing how equipment is physically racked and cabled, is a foundation I will carry into more advanced networking and network-security work, where an accurate picture of the underlying infrastructure is essential to securing it.
