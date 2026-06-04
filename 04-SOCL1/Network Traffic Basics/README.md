# 🌐 Network Traffic Analysis (NTA) Basics - Write-up

## 📝 Overview
This document summarizes the core concepts of Network Traffic Analysis (NTA). NTA is not just about using tools like Wireshark; it's a comprehensive process of capturing, inspecting, and correlating network data to understand communication patterns, monitor performance, and detect malicious activities.

## 🧠 Core Concepts

### Why Analyze Network Traffic?
* **Monitor Performance:** Check for abnormalities, sudden peaks, or network slowdowns.
* **Inspect Communication Content:** Detect data exfiltration (e.g., DNS tunneling) or the transfer of malicious files.
* **SOC Perspectives:** Detect suspicious activity, reconstruct attacks during incident response, and validate alerts.

### The TCP/IP Stack Perspective
Network traffic is observed across different layers of the TCP/IP model:
* **Application Layer:** Contains application headers and payload data (e.g., HTTP GET requests, ZIP file contents).
* **Transport Layer:** Segments data and adds headers (TCP/UDP) including ports and sequence numbers (useful for detecting session hijacking).
* **Internet Layer:** Adds headers like source/destination IP. Important for detecting fragmentation attacks.
* **Link Layer:** Adds MAC addresses. Crucial for detecting attacks like ARP poisoning.

## 🚦 Network Sources and Flows

### Sources
* **Intermediary Devices:** Firewalls, switches, routers (generate lower traffic volumes, mostly routing/management protocols).
* **Endpoint Devices:** Servers, PCs, mobile devices (generate the bulk of network bandwidth).

### Flows
* **North-South Traffic:** Traffic crossing the firewall (LAN to WAN and vice versa). Commonly monitored (e.g., HTTPS, DNS, SSH).
* **East-West Traffic:** Traffic staying within the LAN. Crucial to monitor for lateral movement (e.g., Kerberos, SMB, internal DNS).

## 🪛 Capture and Analysis Methods

### Data Sources
* **Logs:** The first entry point (e.g., Auth logs, Apache access logs). Formats vary by vendor.
* **Full Packet Capture (PCAP):** Capturing the entire packet (headers and payload) for deep inspection.
* **Network Statistics:** Metadata about flows (e.g., NetFlow, IPFIX) used to find anomalies without capturing full packets.

### Full Packet Capture Methods
1.  **Network Tap:** A physical device placed inline that copies all traffic without affecting performance (operates at the link layer).
2.  **Port Mirroring (e.g., SPAN):** A software configuration on an intermediary device (switch/router) that duplicates packets from one port to a monitoring port.

### Scenario Findings (Interactive Lab)
* **Scenario 1 (HTTP Traffic):** `THM{FoundTheMalware}`
    * *Placement:* Between the Web Proxy and the Firewall to capture all outbound HTTP requests.
* **Scenario 2 (DNS Traffic):** `THM{C2CommandFound}`
    * *Placement:* Between the Core Switch and the Internal DNS Server to capture internal DNS queries before they are forwarded.