# 🛡️ TryHackMe: Intro to IDS (Intrusion Detection System)

This repository contains my notes, lab exercises, and practical configurations from the "Intro to IDS" room on TryHackMe. This lab focuses on the fundamentals of Network Monitoring and configuring Snort (an open-source NIDS) for malicious traffic detection and forensic analysis.

## 🎯 Learning Objectives
- Understand the deployment and detection modes of Intrusion Detection Systems.
- Learn the core functionalities and operating modes of **Snort IDS**.
- Create and deploy **Custom Snort Rules** to detect specific network traffic.
- Perform **Forensic Analysis** by running Snort against historical packet capture (`.pcap`) files.

---

## 🧠 Core Concepts

### 1. IDS Categorization
**Deployment Modes:**
- **HIDS (Host-based IDS):** Installed on individual machines to monitor specific host activities.
- **NIDS (Network-based IDS):** Deployed at network boundaries/chokepoints to monitor all incoming and outgoing network traffic.

**Detection Modes:**
- **Signature-Based:** Detects known threats by matching traffic against a database of attack patterns (Signatures). Extremely fast but cannot detect zero-day attacks.
- **Anomaly-Based:** Establishes a baseline of normal network behavior and flags any deviations. Good for detecting zero-day attacks but prone to false positives.
- **Hybrid IDS:** Combines both signature and anomaly-based methods for maximum coverage.

### 2. Snort Operating Modes
- **Packet Sniffer Mode:** Reads and displays real-time network packets on the console (used for troubleshooting).
- **Packet Logging Mode:** Logs network traffic into `.pcap` files for future analysis and forensics.
- **NIDS Mode:** The primary mode. Monitors network traffic in real-time, matches it against defined rules, and generates alerts.

---

## 🛠️ Hands-on Labs & Commands

### 1. Writing Custom Snort Rules
Snort rules are composed of a **Rule Header** (Action, Protocol, IPs, Ports) and **Rule Options** (msg, sid, rev). 

**Task:** Created a custom rule in `/etc/snort/rules/local.rules` to detect ICMP ping requests to the loopback address.
```text
alert icmp any any -> 127.0.0.1 any (msg:"Loopback Ping Detected"; sid:10003; rev:1;)