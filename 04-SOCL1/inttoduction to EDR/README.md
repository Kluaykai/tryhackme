# 🛡️ Introduction to Endpoint Detection and Response (EDR)

A comprehensive guide to understanding how EDR solutions provide deep-level visibility, advanced threat detection, and response capabilities for enterprise endpoints.

## 📌 Overview (ภาพรวม)
While traditional Antivirus (AV) relies primarily on signature-based detection (like an immigration passport check), an **EDR** monitors continuous endpoint behavior (like security officers monitoring CCTV inside the airport). EDR is crucial for detecting advanced, fileless, and zero-day threats that bypass basic AV defenses.

## 🏗️ Architecture (สถาปัตยกรรมหลัก)
*   **Agents (Sensors):** Lightweight software installed on endpoints to monitor activities and collect telemetry data.
*   **EDR Console:** The centralized dashboard where telemetry is aggregated, analyzed via Machine Learning, and presented to SOC analysts.

## 📊 Telemetry Data Collected (ข้อมูลที่ EDR ดึงมาวิเคราะห์)
To make accurate judgments, EDR collects detailed "Black Box" data from endpoints, including:
1.  **Process Executions & Terminations:** Tracks parent-child process relationships (e.g., `winword.exe` spawning `powershell.exe`).
2.  **Network Connections:** Identifies Command and Control (C2) communications and data exfiltration.
3.  **Command Line Activity:** Captures executed commands, including obfuscated scripts.
4.  **Registry Modifications:** Monitors changes to Windows configuration settings often used for malware persistence.
5.  **Files and Folders Modifications:** Tracks malicious file dropping and ransomware staging.

## 🕵️ Advanced Detection Techniques (เทคนิคการตรวจจับ)
*   **Behavioral Detection:** Flags suspicious actions rather than just known bad files (e.g., unusual process spawning).
*   **Anomaly Detection:** Identifies deviations from normal baseline endpoint behavior.
*   **IOC Matching:** Compares files and IPs against known Threat Intelligence feeds (e.g., Hash, Malicious Domains).
*   **MITRE ATT&CK Mapping:** Maps detected activities to specific attacker tactics and techniques.
*   **Machine Learning:** Detects complex, multi-stage attacks that lack individual malicious signatures.

## ⚔️ Response Capabilities (การตอบโต้ภัยคุกคาม)
SOC Analysts can execute these actions directly from the EDR console:
*   **Isolate Host:** Disconnects the infected machine from the network to prevent lateral movement.
*   **Terminate Process:** Force-quits a specific malicious process without disrupting the whole system.
*   **Quarantine:** Moves malicious files to an isolated location to prevent execution.
*   **Remote Access (RTR):** Allows analysts to access the endpoint shell to run scripts or collect forensic artefacts (Memory Dumps, Logs).

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC L1 / Cybersecurity Operations / EDR Analysis