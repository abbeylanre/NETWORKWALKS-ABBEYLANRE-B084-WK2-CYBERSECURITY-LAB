# 🛡️ Networkwalks Cybersecurity Internship — Week 2
**Phase 1 & Phase 2: Reconnaissance, Footprinting & Network Scanning**

[![Internship](https://img.shields.io/badge/Program-Networkwalks_Cybersecurity_Internship-blue)](#)
[![Batch](https://img.shields.io/badge/Batch-B084-informational)](#)
[![Authorization](https://img.shields.io/badge/LOA_Ref-NW--084--178-success)](#)
[![Status](https://img.shields.io/badge/Week_2-Completed-brightgreen)](#)

---

## 📌 Project Overview
This repository documents my practical exercises, technical workflows, OSINT research, and network discovery outcomes completed during **Week 2** of the **Networkwalks Cybersecurity Internship (Batch B084)**.

The objective of this milestone was to simulate the initial phases of an ethical penetration test—progressing from passive and active domain footprinting (`networkwalks.com`) to local area network (LAN) host enumeration and topology mapping (`172.20.10.0/28`).

---

## 📂 Repository Structure & Completed Modules

### 🔹 Elective Modules (Phase 1: Footprinting & OSINT)

| Module | Title & Focus Area | Tools Used | Status | Documentation |
| :--- | :--- | :--- | :---: | :--- |
| **W2-PM1** | Footprinting with Multiple Kali Linux Tools | `whois`, `whatweb`, `nslookup`, `curl`, `wafw00f`, `dnsrecon` | ✅ Completed | [View Folder](PM1-Kali-Footprinting-Tools) |
| **W2-PM3** | Maltego-Based Infrastructure Footprinting | Maltego CE (Transforms & Link Analysis) | ✅ Completed | [View Folder](./W2-PM3/) |
| **W2-PM4** | theHarvester-Based OSINT Enumeration | `theHarvester` | ✅ Completed | [View Folder](./W2-PM4/) |

### 🔸 Essential Modules (Phase 2: Scanning & Final Reporting)

| Module | Title & Focus Area | Tools Used | Status | Documentation |
| :--- | :--- | :--- | :---: | :--- |
| **W2-PM5** | Zenmap-Based Network Scanning & Topology | Zenmap (Nmap 7.993), `ipconfig /all` | ✅ Completed | [View Folder](./W2-PM5/) |
| **W2-PM-FINAL** | Comprehensive Week 2 Penetration Testing Report | All Week 2 Reconnaissance & Scanning Tools | ✅ Completed | [View Report](./W2-PM-FINAL/) |

---

## 🔍 Key Technical Highlights & Findings
* **Domain & Web Stack Fingerprinting (`W2-PM1`):** Resolved target infrastructure (`192.232.216.135`), identified CMS/plugin versions (WordPress `7.0.4`, WP Download Manager `3.3.58`), inspected HTTP headers (`/wp-json/`), detected ModSecurity WAF, and enumerated DNS records (`NS`, `MX`, `TXT/SPF`, `SRV`).
* **OSINT & Entity Mapping (`W2-PM3` & `W2-PM4`):** Correlated domain entities, netblocks, subdomains, and publicly indexed contact information using graphical link analysis and passive search engines.
* **Local Subnet Discovery (`W2-PM5`):** Audited active host interface (`172.20.10.3` on subnet `172.20.10.0/28`), enumerated **2 live hosts** (`172.20.10.1` and `172.20.10.3`), mapped MAC addresses, identified open TCP services, and exported the network topology diagram (`subnet-topology.pdf`).

---

## 🗂️ Standard Module Documentation Structure
Each module directory in this repository follows a standardized reporting structure:
* **Project Objectives & Scope**
* **Tools & Environment Configuration**
* **Step-by-Step Procedures & Commands**
* **Screenshots & Raw Evidence (`screenshots/`)**
* **Findings, Risk Analysis & Recommendations**
* **Challenges Encountered & Lessons Learned**

---

## 🎯 Core Learning Outcomes
* **Structured Reconnaissance:** Understanding how attackers chain passive OSINT and active enumeration tools before attempting exploitation.
* **Web & DNS Attack Surface Analysis:** Identifying exposed technology versions, HTTP response headers, WAF protections, and DNS misconfigurations.
* **Layer 2 & Layer 3 Network Discovery:** Conducting host discovery via ARP/ICMP/TCP probes and visualizing network hops in Zenmap.
* **Professional Security Reporting:** Translating raw technical output into structured, risk-rated findings and actionable remediation advice.

---

## ⚖️ Authorization & Security Disclaimer
> **Strict Scope & Ethical Compliance:** All reconnaissance and scanning activities documented in this repository were conducted strictly within authorized boundaries under written **Letter of Authorization (`Ref: NW-084-178`, valid 13 Nov 2026 – 20 Nov 2026)** for `networkwalks.com` and on the tester's own local area network (`172.20.10.0/28`). All materials are shared strictly for educational and defensive cybersecurity purposes.

---

## 👤 Author
* **Name:** Abiodun Omotosho (`Abbeylanre`)
* **Program:** Networkwalks Cybersecurity Internship — Batch B084
* **Milestone:** Week 2 (Footprinting & Network Scanning)
