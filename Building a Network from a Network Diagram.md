# Building a Network from a Network Diagram

**Cisco Packet Tracer · Physical Mode · CCNA-aligned**

**Prepared by:** Osita Kingsley Odo
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

<img width="940" height="650" alt="image" src="https://github.com/user-attachments/assets/1f48a454-9dae-41ce-a208-02887ac5574d" />


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

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/a693a488-3364-48a8-8b1c-a734f1b4b900" />


*Figure 2 — Equipment rack cabled in Physical Mode, with the straight-through cable highlighted on the pegboard.*

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/608578a0-f7f9-4773-9348-41ff3e40a52e" />


*Figure 3 — PC-A and PC-B cabled at the workbench, completing the end-device connections.*

## Verification & Result

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/21826983-771d-480f-a20c-7243559051c8" />

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

The most valuable part of this exercise was the discipline of documenting every connection before building anything. Mapping the logical diagram to a precise device table made the physical build fast [...]
