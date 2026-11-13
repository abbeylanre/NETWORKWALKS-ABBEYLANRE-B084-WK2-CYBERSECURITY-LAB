# W2-PM5: Network Scanning with Zenmap

## 1. Project Overview

This project explores network scanning and host discovery using **Zenmap**, the official graphical user interface (GUI) for Nmap. The lab focuses on discovering live hosts within a local area network (LAN) subnet, identifying IPv4 and MAC address mappings, mapping network topology, and exporting visual scan graphics for documentation and audit purposes.

---

## 2. Objectives

* Install and configure Zenmap on a desktop environment.
* Determine local network interface parameters, including the local IP address and LAN subnet boundary.
* Execute an automated Ping Scan across the local subnet (`/24`) to enumerate active network hosts.
* Extract operational network metrics including live host counts, IP allocations, and MAC addresses.
* Render, analyze, and export the network topology map into PDF format.

---

## 3. Tools and Technologies

| Component | Details |
| :--- | :--- |
| **Primary Tool** | Zenmap GUI (Nmap Frontend) |
| **Utilities** | Windows Command Prompt (`cmd.exe`), `ipconfig` / `ipconfig /all` |
| **Operating System** | Windows / Multi-platform |
| **Scan Profile** | Ping Scan (`nmap -sn`) |
| **Target Subnet** | `10.0.0.0/24` (Local Area Network) |

---

## 4. Practical Exercises

### Task 1: Download & Install Zenmap

* **Purpose:** Install Zenmap GUI and Nmap dependencies on the local machine.
* **Procedure:**
  1. Downloaded the official setup installer from [nmap.org/download.html](https://nmap.org/download.html).
  2. Executed the setup wizard, accepting default component options (Nmap, Zenmap GUI, Npcap drivers).
  3. Completed installation and launched the Zenmap GUI application interface.

* **Screenshots & Evidence:**  
  ![Zenmap Installation](./Screenshots/01-zenmap-installation.png)

---

### Task 2: Network Parameter Discovery

* **Purpose:** Identify the local host's IPv4 address, subnet mask, and local network range using CLI utilities.
* **Command Executed:**
  ```cmd
  ipconfig /all
Results Obtained:

Local Host IP Address: 10.0.0.5

Subnet Mask: 255.255.255.0 (/24)

Target LAN Subnet: 10.0.0.0/24

Local MAC Address: 00-0C-29-40-C0-93

Screenshots & Evidence:

Task 3: Subnet Live Host Discovery Scan
Purpose: Perform a non-intrusive Ping Scan (-sn) across the 10.0.0.0/24 subnet to identify all operational network endpoints.

Zenmap Configuration:

Target Range: 10.0.0.0/24

Selected Profile: Ping scan

Generated Nmap Command:

Bash
nmap -sn 10.0.0.0/24
Screenshots & Evidence:

Tasks 4, 5 & 6: Live Host Enumeration & Hardware Addressing
The ping scan successfully enumerated active endpoints across the target subnet. Findings are itemized below:

Task 4: Total Live Hosts: 4 hosts live (including local host).

Task 5 & 6: IP and MAC Address Mapping:

Host #	IPv4 Address	MAC Address	Interface / Hardware Vendor
Host 1	10.0.0.1	00:50:56:E3:B3:2C	Gateway / Virtual Interface
Host 2	10.0.0.4	00:0C:29:C0:94:8F	Network Host
Host 3	10.0.0.19	00:50:56:E9:64:82	Network Host
Host 4	10.0.0.5	00-0C-29-40-C0-93	Local Host (Host System)
Screenshots & Evidence:

Task 7: Network Topology Render & PDF Export
Purpose: Generate a graphical topology representation of discovered subnet endpoints and export the diagram for report integration.

Procedure:

Clicked the Topology tab within Zenmap.

Enabled the map Legend to evaluate node connections, latency rings, and hop counts.

Selected Save Graphic and chose PDF format.

Saved the exported graphic file (subnet-topology.pdf) to the Desktop.

Screenshots & Evidence:

5. Findings and Analysis
Subnet Density: Out of 254 usable host addresses on the 10.0.0.0/24 subnet, exactly 4 active nodes were detected.

MAC Resolution Mechanism: ARP queries initiated during local subnet scans allowed Zenmap/Nmap to resolve exact MAC addresses for remote nodes on the same Layer 2 broadcast domain.

Visual Mapping Advantage: Zenmap's topology rendering provides immediate visualization of host clustering around the default gateway (10.0.0.1), aiding in rapid attack surface visualization.

6. Challenges Encountered
Local Firewall Interference: Host-based firewalls on Windows targets may drop standard ICMP echo requests.

Mitigation: Zenmap sends combined ICMP echo requests alongside TCP ACK probes to TCP port 80 and SYN probes to TCP port 443 to reliably detect live hosts.

MAC Address Enumeration Boundaries: Local host MAC address resolution requires ipconfig /all because operating system networking stacks bypass standard Layer 2 ARP lookups for the local loopback interface.

7. Lessons Learned
GUI vs. CLI Workflows: Zenmap simplifies Nmap profile management for repetitive scans while adding graphical benefits such as visual network topology maps and searchable output filters.

Layer 2 Scan Accuracy: Local subnet scans leverage ARP requests (-PR), providing faster and more reliable host detection than internet-routable IP scans.

Passive Identification via MACs: Organizationally Unique Identifiers (OUIs) contained within the first three octets of MAC addresses (e.g., 00:50:56 for VMware) allow security analysts to identify virtualized environments quickly.

8. Conclusion
The Zenmap scanning module successfully demonstrated host discovery, hardware address mapping, and subnet topology visualization across the target LAN (10.0.0.0/24). The lab verified the operational state of 4 active hosts and documented network topology metrics in PDF report format.

Security Disclaimer
All scanning activities were conducted strictly for educational purposes within a controlled laboratory environment in accordance with ethical cybersecurity standards.

👤 Author Metadata

Name: Abiodun Omotosho

Prpment, practical achievements, and professional growth in cybersecurity.
