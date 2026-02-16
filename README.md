<p align="center">
  <img src="https://www.especial.gr/wp-content/uploads/2019/03/panepisthmio-dut-attikhs.png" alt="UNIWA" width="150"/>
</p>

<p align="center">
  <strong>UNIVERSITY OF WEST ATTICA</strong><br>
  SCHOOL OF ENGINEERING<br>
  DEPARTMENT OF COMPUTER ENGINEERING AND INFORMATICS
</p>

---

<p align="center">
  <strong>Computer Networks II</strong>
</p>

<h1 align="center">
  OSPF Routing
</h1>

<p align="center">
  <strong>Vasileios Evangelos Athanasiou</strong><br>
  Student ID: 19390005
</p>

<p align="center">
  <a href="https://github.com/Ath21" target="_blank">GitHub</a> ·
  <a href="https://www.linkedin.com/in/vasilis-athanasiou-7036b53a4/" target="_blank">LinkedIn</a>
</p>

<p align="center">
  Supervisor: Adonis Bogris, Professor<br>
</p>

<p align="center">
  <a href="https://ice.uniwa.gr/en/emd_person/adonis-bogris/" target="_blank">UNIWA Profile</a> ·
  <a href="https://www.linkedin.com/in/adonis-bogris-baa6803a/" target="_blank">LinkedIn</a>
</p>

<p align="center">
  Co-supervisor: Rania Garofalaki, Laboratory Teaching Staff<br>
</p>

<p align="center">
  <a href="https://ice.uniwa.gr/en/emd_person/zacharenia-garofalaki/" target="_blank">UNIWA Profile</a> ·
  <a href="https://www.linkedin.com/in/rania-garofalaki-4761b071/" target="_blank">LinkedIn</a>
</p>

<p align="center">
  Athens, May 2022
</p>

---

# Project Overview

The primary objective of this project was to establish **full IP connectivity within Autonomous System (AS) 20** using the **OSPF routing protocol**.  
The network architecture was designed using multiple OSPF areas:

- **Area 0 (Backbone Area)**
- **Area 10**
- **Area 20**

These areas are interconnected through **Area Border Routers (ABRs)**, ensuring proper inter-area routing and adherence to OSPF hierarchical design principles.

---

## Table of Contents

| Section | Folder / File | Description |
|------:|---------------|-------------|
| 1 | `assign/` | Assignment material |
| 1.1 | `assign/OSPF - homework_NetworksII.pdf` | Assignment description in English |
| 1.2 | `assign/OSPF - homework_ΔίκτυαΙΙ.pdf` | Assignment description in Greek |
| 2 | `docs/` | Project documentation |
| 2.1 | `docs/OSPF_Routing.pdf` | OSPF routing analysis and configuration (English) |
| 2.2 | `docs/OSPF_Δρομολόγηση.pdf` | OSPF routing analysis and configuration (Greek) |
| 3 | `src/` | Source files |
| 3.1 | `src/OSPF.pkt` | Cisco Packet Tracer topology and OSPF configuration |
| 4 | `README.md` | Repository overview and usage instructions |

---

## Network Configuration Details

### 1. OSPF Process Configuration

OSPF was configured on each router by defining:
- A **process ID**
- A **unique Router ID**
- The participating **subnets** and their corresponding **OSPF areas**

#### Router IDs Used

- **R1:** `1.1.1.1`
- **ABR2:** `2.2.2.2`
- **ABR3:** `3.3.3.3`
- **R4:** `4.4.4.4`
- **R5:** `5.5.5.5`

---

### 2. Implementation Steps

The following Cisco IOS CLI commands were used during router configuration:

- `router ospf <process-id>`  
  Initiates the OSPF routing process.

- `router-id <address>`  
  Assigns a unique identifier to the router.

- `network <ip-address> <wildcard-mask> area <area-id>`  
  Specifies which interfaces and subnets participate in OSPF and assigns them to the appropriate area.

- `passive-interface <interface>`  
  Configured on **R4** and **R5** (interface `FastEthernet0/1`) to prevent the transmission of OSPF updates toward non-router end devices.

---

### 3. Route Summarization

To improve routing efficiency and reduce the size of routing tables, **inter-area route summarization** was implemented on the ABRs.

#### Summarized Routes

- **Area 10 Summary:**  
  `172.16.32.0/23`  
  (Summarizes `172.16.32.0/24` and `172.16.33.0/24`)

- **Area 20 Summary:**  
  `174.18.30.0/23`  
  (Summarizes `174.18.30.0/24` and `174.18.31.0/24`)

- **Area 0 Summary:**  
  `173.17.36.0/22`  
  (Summarizes `173.17.37.0/24`, `173.17.38.0/24`, and `173.17.39.0/24`)

---

## Verification Commands

The following commands were used to verify the correct operation of OSPF:

- `show running-config`  
  Confirms the applied OSPF configuration.

- `show ip route`  
  Displays the routing table and verifies **inter-area (O IA)** routes.

- `show ip ospf neighbor`  
  Examines OSPF neighbor relationships and adjacency states (e.g., **FULL/DR**, **FULL/BDR**).

- `show ip ospf database`  
  Inspects the **Link State Database (LSDB)** and the different **LSA types**.

---

# Installation & Setup Guide

This project is implemented using **Cisco Packet Tracer** and demonstrates **multi-area OSPF routing**.  
No compilation or programming environment is required.

---

## Prerequisites

### Software
- **Cisco Packet Tracer** (version **7.3 or newer** recommended)
  - Must support:
    - OSPF routing
    - Multi-area OSPF
    - Route summarization
- **Operating System**
  - Windows 10 / 11
  - Linux
  - macOS

> Cisco Packet Tracer is available for free to students via **Cisco Networking Academy (NetAcad)**.

---

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/Computer-Networks-2/OSPF.git
```

Alternatively, download the repository as a **ZIP file** and extract it locally.

---

## Project Structure

After cloning or extracting the repository, the relevant file is located at:

```bash
src/OSPF.pkt
```

This file contains:
- The complete network topology
- Router interface configurations
- OSPF processes and area assignments
- Route summarization on Area Border Routers (ABRs)

---

## Setup Instructions

### Open the Project in Cisco Packet Tracer

1. Launch **Cisco Packet Tracer**
2. Select **File → Open**
3. Navigate to:
```bash
src/OSPF.pkt
```
4. Open the file and wait for the topology to fully load

---

## Verify Router Configuration 

To inspect or validate the OSPF configuration:

1. Click on any router (R1, ABR2, ABR3, R4, R5)
2. Open the **CLI** tab
3. Execute the following commands:

```bash
show running-config
show ip ospf
show ip ospf neighbor
show ip route
```
These commands verify:
- OSPF process activation
- Router IDs
- Neighbor adjacencies
- Inter-area routing entries (O IA)

---

## Testing & Validation
### Connectivity Testing
- Use Ping between hosts in different OSPF areas
- Confirm full IP connectivity across:
    - Area 0 (Backbone)
    - Area 10
    - Area 20

### Routing Validation
- Ensure routes are learned dynamically via OSPF
- Verify summarized routes appear on ABRs
- Confirm that no unnecessary specific routes propagate between areas

--- 

## Troubleshooting
### OSPF neighbors not forming
- Check interface status (up/up)
- Verify correct area IDs
- Confirm matching subnet masks and wildcard masks

### Missing routes
- Verify OSPF network statements
- Check summarization configuration on ABRs

### End devices receiving OSPF updates
- Ensure passive-interface is configured on access-facing interfaces

---

## Open the Documentation
1. Navigate to the docs/ directory
2. Open the report corresponding to your preferred language:
    - English: `OSPF_Routing.pdf`
    - Greek: `OSPF_Δρομολόγηση.pdf`