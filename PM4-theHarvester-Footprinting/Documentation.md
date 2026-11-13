# W2-PM4: Footprinting & Reconnaissance Attacks with theHarvester

## 1. Project Overview

This project focuses on executing passive Open-Source Intelligence (OSINT) and footprinting using **theHarvester** in Kali Linux. The exercise demonstrates how security analysts gather email addresses, subdomains, employee names, and host details from public data sources without directly interacting with the target organization.

---

## 2. Objectives

* Understand the role of passive reconnaissance in cybersecurity assessments.
* Learn how to configure and execute `theHarvester` using targeted search engines and multi-source modes.
* Harvest publicly exposed email IDs, subdomains, and host infrastructure.
* Analyze security risks associated with public information leakage and missing API configurations.
* Document findings and propose defensive measures to reduce an organization's digital footprint.

---

## 3. Tools and Technologies

| Component | Details |
| :--- | :--- |
| **Primary Tool** | `theHarvester` (v4.11.1) |
| **Operating System** | Kali Linux |
| **Environment** | Command-Line Interface (CLI) |
| **Data Sources** | Baidu, Hudson Rock, CRT.sh, DuckDuckGo, Hackertarget, and 30+ Public Providers |
| **Target Scope** | `microsoft.com` (Educational Demonstration Scope) |

---

## 4. Practical Exercises

### Task 1: Passive Reconnaissance Using a Specific Engine (Baidu)

* **Purpose:** Gather email addresses and subdomains from a single targeted search engine source with a specified result limit.
* **Availability:** Pre-installed in Kali Linux (`theHarvester`).
* **Target & Scope:** `microsoft.com` (Educational Scope)

* **Command Executed:**
  ```bash
  theHarvester -d microsoft.com -l 1000 -b baidu
Command Syntax Breakdown:

-d microsoft.com: Specifies the target domain.

-l 1000: Limits the query results to 1000 entries.

-b baidu: Sets the data source engine to Baidu.

Results Obtained:

Plaintext
*******************************************************************
* theHarvester 4.11.1                                             *
* Coded by Christian Martorella                                   *
*******************************************************************
[*] Target: microsoft.com 
[*] Searching Baidu. 

[*] No IPs found.
[*] No emails found.
[*] No people found.
[*] No hosts found.
Screenshots & Evidence:

Observations: Querying regional search engines like Baidu for a major Western enterprise (microsoft.com) yielded zero results due to geographic indexing limitations and anti-scraping controls.

Task 2: Multi-Source Aggregated Reconnaissance (all Sources)
Purpose: Aggregate intelligence across all supported public search engines, certificate logs, and threat intelligence databases.

Availability: Pre-installed in Kali Linux (theHarvester).

Target & Scope: microsoft.com (Educational Scope)

Command Executed:

Bash
theHarvester -d microsoft.com -l 50 -b all
Command Syntax Breakdown:

-d microsoft.com: Specifies the target domain.

-l 50: Limits the query results per source to 50 entries.

-b all: Executes queries across all default and supported search engines and databases.

Results Obtained:

API Restrictions Encountered: Commercial modules requiring dedicated API keys (bevigil, censys, shodan, virustotal, hunter, etc.) returned [!] Missing API key errors, forcing the tool to skip them or fall back to unauthenticated scraping modes.

Successful Unauthenticated Modules:

Hudson Rock: Processed domain telemetry for microsoft.com, reporting domain breach statistics (621,809 total compromised, 16,601 employees, 600,418 users) and extracting 44 hosts from employee URLs.

Windvane (DNS Fallback): Executed subdomain pattern searches when API services were unavailable, identifying 14 subdomains via DNS fallback.

Additional Public Sources Queried: Chaos, Certspotter, Baidu, DuckDuckGo, CRT.sh, Hackertarget, Commoncrawl, LeakIX, Mojeek, Otx, Rapiddns, Robtex, ShodanInternetDB, Subdomaincenter, Thc, Threatcrowd, Subdomainfinderc99, Urlscan, and Yahoo.

Screenshots & Evidence:

Observations: Running theHarvester against all sources highlights the value of unauthenticated public repositories—such as Certificate Transparency logs (crt.sh), DNS fallback patterns, and breach telemetry aggregators like Hudson Rock—when commercial API keys are unconfigured.

5. Findings and Analysis
Passive reconnaissance using theHarvester against microsoft.com revealed several key technical insights:

Impact of Missing API Keys: Modern versions of theHarvester rely heavily on API integrations for commercial threat intelligence platforms (such as Shodan, VirusTotal, and SecurityTrails). Without configured keys in /etc/theHarvester/api-keys.yaml, enumeration is restricted to public scraping and fallback mechanisms.

Value of Alternative Enumeration: Despite API limitations, fallback routines—such as Hudson Rock extracting 44 employee-linked hosts and DNS fallback harvesting 14 subdomains—successfully mapped external corporate assets without requiring authentication.

Zero-Touch Reconnaissance: Because all queries targeted public registries, certificate logs, and third-party threat aggregators rather than Microsoft's production infrastructure, the reconnaissance remained entirely passive and undetectable by target Intrusion Detection Systems (IDS).

6. Challenges Encountered
API Authentication Barriers: Numerous data modules failed due to missing or unconfigured API keys in /etc/theHarvester/api-keys.yaml.

Rate-Limiting & Engine Blocks: Large enterprise targets trigger strict rate-limiting and automated bot defenses on public search engines, causing engines like Baidu to return empty result sets.

Process Execution Management: Sweeping all supported data sources significantly increases runtime, requiring manual job control (Ctrl + Z) during extended terminal execution.

7. Lessons Learned
Tool Configuration Matters: Populating /etc/theHarvester/api-keys.yaml with valid API keys unlocks deeper intelligence across commercial data providers.

Resilience of Fallback Modules: Even without paid API access, open data sources like Certificate Transparency logs and DNS fallback routines yield actionable baseline reconnaissance.

Attack Surface Awareness: Publicly indexed breach telemetry and exposed employee hostnames represent critical intelligence vectors that security teams must continuously monitor and remediate.

8. Conclusion
This exercise demonstrated how to conduct passive OSINT footprinting using theHarvester in Kali Linux. By executing both targeted single-engine queries (baidu) and broad multi-source sweeps (all), we evaluated how reconnaissance tools map external attack surfaces while navigating API dependencies and anti-scraping defenses.

## Security Disclaimer
All footprinting activities were conducted strictly for educational purposes using publicly available information sources in accordance with ethical cybersecurity standards.

## 👤 Author Metadata

Name: Abiodun Omotosho

Program: Networkwalks Cybersecurity Internship

Focus Areas: Cybersecurity | Network Security | SOC Analyst | Penetration Testing

LinkedIn: Abiodun Omotosho Profile

This repository serves as a live record of my technical development, practical achievements, and professional growth in cybersecurity.
