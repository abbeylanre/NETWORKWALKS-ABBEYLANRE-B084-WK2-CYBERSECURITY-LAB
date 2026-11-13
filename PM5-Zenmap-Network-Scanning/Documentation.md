# W2-PM5: Network Scanning with Zenmap

## 1. Project Overview

This project explores network scanning and host discovery using **Zenmap**, the official graphical user interface (GUI) for Nmap. The lab focuses on discovering live hosts within a local area network (LAN) subnet, identifying IPv4 and MAC address mappings, mapping network topology, and exporting visual scan graphics for documentation and audit purposes.

---

## 2. Objectives

* Install and configure Zenmap on a desktop environment.
* Determine local network interface parameters, including the local IP address and LAN subnet boundary.
* Execute an automated Ping Scan across the local subnet (`/28` / `/24`) to enumerate active network hosts.
* Extract operational network metrics including live host counts, IP allocations, and MAC addresses.
* Render, analyze, and export the network topology map into PDF format.

---

## 3. Tools and Technologies

| Component | Details |
| :--- | :--- |
| **Primary Tool** | Zenmap GUI (Nmap 7.993 Frontend) |
| **Utilities** | Windows Command Prompt (`cmd.exe`), `ipconfig` / `ipconfig /all` |
| **Operating System** | Windows |
| **Scan Profile** | Ping Scan (`nmap -sn`) / Regular Scan |
| **Target Subnet** | `172.20.10.0/28` (Active Wi-Fi LAN; scanned across `172.20.10.0/24`) |

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

Active Interface: Wireless LAN adapter Wi-Fi (Intel Dual Band Wireless-AC 8265)

Local Host IP Address: 172.20.10.3

Subnet Mask: 255.255.255.240 (/28)

Target LAN Subnet: 172.20.10.0/28

Default Gateway: 172.20.10.1

Local MAC Address: E4-70-B8-81-BE-15

Screenshots & Evidence:

Task 3: Subnet Live Host Discovery Scan
Purpose: Perform a non-intrusive host discovery scan across the 172.20.10.0 network range to identify all operational network endpoints.

Zenmap Configuration:

Target Range: 172.20.10.0/24 (covering local /28 subnet 172.20.10.0/28)

Selected Profile: Ping scan / Regular scan

Generated Nmap Command:

Bash
nmap -sn 172.20.10.0/28
Screenshots & Evidence:

Tasks 4, 5 & 6: Live Host Enumeration & Hardware Addressing
The scan successfully enumerated active endpoints across the target subnet. Findings are itemized below:

Task 4: Total Live Hosts: 2 hosts live (including the local host).

Task 5 & 6: IP and MAC Address Mapping:

Host #	IPv4 Address	MAC Address	Interface / Role & Open Ports
Host 1	172.20.10.1	86:AD:8D:E8:5D:64	Default Gateway / Router (21/tcp ftp, 53/tcp domain, 49152/tcp)
Host 2	172.20.10.3	E4-70-B8-81-BE-15	Local Host / Tester PC (135/tcp msrpc, 139/tcp netbios-ssn, 445/tcp microsoft-ds)
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
Subnet Density: Across the scanned IP range (256 total addresses scanned, 14 usable host addresses in the active /28 subnet), exactly 2 active nodes were detected (172.20.10.1 and 172.20.10.3).

MAC Resolution Mechanism: ARP queries initiated during local subnet scans allowed Zenmap/Nmap to resolve the exact MAC address (86:AD:8D:E8:5D:64) for the remote gateway node (172.20.10.1) on the same Layer 2 broadcast domain.

Visual Mapping Advantage: Zenmap's topology rendering provides immediate visualization of host clustering around the default gateway (172.20.10.1), aiding in rapid attack surface visualization.

6. Challenges Encountered
Local Firewall Interference: Host-based firewalls on Windows targets may drop standard ICMP echo requests.

Mitigation: Zenmap sends combined ICMP echo requests alongside TCP ACK probes to TCP port 80 and SYN probes to TCP port 443 to reliably detect live hosts.

MAC Address Enumeration Boundaries: Local host MAC address resolution requires ipconfig /all (E4-70-B8-81-BE-15) because operating system networking stacks bypass standard Layer 2 ARP lookups for the local host interface (172.20.10.3).

7. Lessons Learned
GUI vs. CLI Workflows: Zenmap simplifies Nmap profile management for repetitive scans while adding graphical benefits such as visual network topology maps and searchable output filters.

Layer 2 Scan Accuracy: Local subnet scans leverage ARP requests (-PR), providing faster and more reliable host detection than internet-routable IP scans.

Passive Identification via MACs: Organizationally Unique Identifiers (OUIs) or locally administered MAC bits (such as 86:AD:8D on the gateway hotspot) allow security analysts to distinguish mobile/randomized hotspots from standard enterprise network hardware.

8. Conclusion
The Zenmap scanning module successfully demonstrated host discovery, hardware address mapping, and subnet topology visualization across the target LAN (172.20.10.0/28). The lab verified the operational state of 2 active hosts (172.20.10.1 and 172.20.10.3) and documented network topology metrics in PDF report format.

Security Disclaimer
All scanning activities were conducted strictly for educational purposes within a controlled laboratory environment under written authorization (NW-084-178) in accordance with ethical cybersecurity standards.

👤 Author Metadata
Name: Abiodun Omotosho

Program: Networkwalks Cybersecurity Internship (Batch B084)

Focus: Hands-on security assessment, practical achievements, and professional growth in cybersecurity.
