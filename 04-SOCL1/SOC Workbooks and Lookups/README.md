# SOC Investigation: Workbooks and Lookups

A comprehensive guide and documentation of the methodologies used for alert triage, identity/asset lookups, and the implementation of SOC workbooks in a security operations environment.

## 📌 Overview
This repository documents the essential skills required for a SOC Analyst to perform effective alert triage. It focuses on gathering context through asset/identity inventories and following standardized workbooks to ensure consistent and accurate investigations.

## 🎯 Learning Objectives
* **Asset & Identity Enrichment:** Understanding how to use corporate databases to identify users and systems.
* **Network Context:** Leveraging network diagrams to understand traffic flow and potential lateral movement.
* **Standardized Workflows:** Implementing SOC Workbooks (Playbooks) to streamline the triage process.
* **Evidence Collection:** Gathering technical artifacts for escalation and reporting.

## 🔍 Investigation Methodology
The triage process follows a structured three-phase approach:

| Phase | Description | Key Actions |
| :--- | :--- | :--- |
| **Enrichment** | Gathering context about the entities involved. | Check Identity Inventory, Asset Inventory, and Threat Intelligence (TI). |
| **Investigation** | Analyzing the actual behavior and logs. | Build process trees, check SIEM logs, and analyze artifacts (EML, Binaries). |
| **Escalation** | Finalizing the verdict and reporting. | Document findings, reach out to users, or escalate to Level 2 (L2) analysts. |

---

## 🛠️ Scenario-Based Workbooks

### 1. Email Analysis Workbook
Focuses on identifying phishing attempts and malicious attachments.
* **Context:** Identity lookup for recipients.
* **Analysis:** EML header analysis (SPF/DKIM/DMARC) and Sandbox execution.
* **Verification:** Checking for subsequent suspicious login events.

### 2. PowerShell Analysis Workbook
Focuses on detecting malicious script execution.
* **Context:** Asset lookup for the affected host.
* **Analysis:** Process tree construction to find the Parent Process and execution context.
* **Intelligence:** Analyzing URLs or domains contacted by the script.

### 3. Network Analysis Workbook
Focuses on identifying internal/external scanning and potential reconnaissance.
* **Context:** Network mapping to identify source and destination zones.
* **Analysis:** Port scanning pattern identification and service discovery.
* **Validation:** Differentiating between legitimate security scanners (Nessus/Zabbix) and attackers.

---

## 🏗️ Key Components

### Identity Inventory
A catalogue of corporate employees and services.
* **Data Points:** Full Name, Role, Location, Access Privileges.
* **Sources:** Active Directory (AD), Okta, BambooHR.

### Asset Inventory
A list of all computing resources within the IT environment.
* **Data Points:** Hostname, IP Address, OS, Owner, Purpose.
* **Sources:** MS Intune, CrowdStrike, Elastic SIEM.

---

## 🚀 Conclusion
Consistent alert triage relies on the synergy between high-quality data (Lookups) and structured procedures (Workbooks). This approach reduces the Mean Time to Respond (MTTR) and ensures that security incidents are handled according to industry best practices.

---
**Author:** Piyangkoon Tongrujiroj
**Focus:** SOC L1 / Cybersecurity Operations