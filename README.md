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

# README

## OSPF Routing

The primary objective of this project was to establish **full IP connectivity within Autonomous System (AS) 20** using the **OSPF routing protocol**.  
The network architecture was designed using multiple OSPF areas:

- **Area 0 (Backbone Area)**
- **Area 10**
- **Area 20**

These areas are interconnected through **Area Border Routers (ABRs)**, ensuring proper inter-area routing and adherence to OSPF hierarchical design principles.

---

## Table of Contents

| Section | Folder / File                           | Description                                         |
| ------: | --------------------------------------- | --------------------------------------------------- |
|       1 | `assign/`                               | Assignment material                                 |
|     1.1 | `assign/OSPF - homework_NetworksII.pdf` | Assignment description in English                   |
|     1.2 | `assign/OSPF - homework_ΔίκτυαΙΙ.pdf`   | Assignment description in Greek                     |
|       2 | `docs/`                                 | Project documentation                               |
|     2.1 | `docs/OSPF_Routing.pdf`                 | OSPF routing analysis and configuration (English)   |
|     2.2 | `docs/OSPF_Δρομολόγηση.pdf`             | OSPF routing analysis and configuration (Greek)     |
|       3 | `src/`                                  | Source files                                        |
|     3.1 | `src/OSPF.pkt`                          | Cisco Packet Tracer topology and OSPF configuration |
|       4 | `README.md`                             | Project documentation                               |
|       5 | `INSTALL.md`                            | Usage instructions                                  |

---

## 1.Network Configuration Details

### 1.1 OSPF Process Configuration

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

## 2. Implementation Steps

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

## 3. Route Summarization

To improve routing efficiency and reduce the size of routing tables, **inter-area route summarization** was implemented on the ABRs.

### 3.1 Summarized Routes

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

## 4. Verification Commands

The following commands were used to verify the correct operation of OSPF:

- `show running-config`  
  Confirms the applied OSPF configuration.

- `show ip route`  
  Displays the routing table and verifies **inter-area (O IA)** routes.

- `show ip ospf neighbor`  
  Examines OSPF neighbor relationships and adjacency states (e.g., **FULL/DR**, **FULL/BDR**).

- `show ip ospf database`  
  Inspects the **Link State Database (LSDB)** and the different **LSA types**.
