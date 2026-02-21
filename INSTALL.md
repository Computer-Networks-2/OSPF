<p align="center">
  <img src="https://www.especial.gr/wp-content/uploads/2019/03/panepisthmio-dut-attikhs.png" alt="UNIWA" width="150"/>
</p>

<p align="center">
  <strong>UNIVERSITY OF WEST ATTICA</strong><br>
  SCHOOL OF ENGINEERING<br>
  DEPARTMENT OF COMPUTER ENGINEERING AND INFORMATICS
</p>

<p align="center">
  <a href="https://www.uniwa.gr" target="_blank">University of West Attica</a> ·
  <a href="https://ice.uniwa.gr" target="_blank">Department of Computer Engineering and Informatics</a>
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

<hr>

<p align="center">
  <strong>Supervision</strong>
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

</hr>

---

<p align="center">
  Athens, May 2022
</p>

---

<p align="center">
  <img src="https://s8182.pcdn.co/wp-content/uploads/2014/07/070214_1756_OSPFpart11.jpg" width="250"/>
</p>

---

# INSTALL

## OSPF Routing

This project is implemented using **Cisco Packet Tracer** and demonstrates **multi-area OSPF routing**.  
No compilation or programming environment is required.

---

## 1. Prerequisites

### 1.1 Software

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

## 2. Installation

### 2.1 Clone the Repository

```bash
git clone https://github.com/Computer-Networks-2/OSPF.git
```

Alternatively, download the repository as a **ZIP file** and extract it locally.

---

## 3. Project Structure

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

## 4. Setup Instructions

### 4.1 Open the Project in Cisco Packet Tracer

1. Launch **Cisco Packet Tracer**
2. Select **File → Open**
3. Navigate to:

```bash
src/OSPF.pkt
```

4. Open the file and wait for the topology to fully load

---

## 5. Verify Router Configuration

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

## 6. Testing & Validation

### 6.1 Connectivity Testing

- Use Ping between hosts in different OSPF areas
- Confirm full IP connectivity across:
  - Area 0 (Backbone)
  - Area 10
  - Area 20

### 6.2 Routing Validation

- Ensure routes are learned dynamically via OSPF
- Verify summarized routes appear on ABRs
- Confirm that no unnecessary specific routes propagate between areas

---

## 7. Troubleshooting

### 7.1 OSPF neighbors not forming

- Check interface status (up/up)
- Verify correct area IDs
- Confirm matching subnet masks and wildcard masks

### 7.2 Missing routes

- Verify OSPF network statements
- Check summarization configuration on ABRs

### 7.3 End devices receiving OSPF updates

- Ensure passive-interface is configured on access-facing interfaces

---

## 8. Open the Documentation

1. Navigate to the docs/ directory
2. Open the report corresponding to your preferred language:
   - English: `OSPF_Routing.pdf`
   - Greek: `OSPF_Δρομολόγηση.pdf`
