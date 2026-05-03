# 📊 SOC Metrics & Performance Evaluation

A comprehensive summary of Security Operations Center (SOC) metrics, Service Level Agreements (SLAs), and strategies for improving team efficiency and reducing alert fatigue.

## 📌 Overview
Measuring the efficiency of a SOC team is critical to ensuring that digital assets remain secure. This guide outlines the key performance indicators (KPIs) used to evaluate SOC operations and the steps required to remediate systemic issues like high False Positive rates and delayed incident response.

## 🎯 Key SOC Metrics

| Metric | Formula / Definition | Target / Ideal State |
| :--- | :--- | :--- |
| **Alerts Count (AC)** | Total Count of Alerts Received | 5 - 30 alerts per day per L1 analyst. |
| **False Positive Rate (FPR)** | False Positives / Total Alerts | As low as possible. **> 80% requires immediate tuning.** |
| **Alert Escalation Rate (AER)** | Escalated Alerts / Total Alerts | Below 20% - 50% (indicates L1 independence). |
| **Threat Detection Rate (TDR)** | Detected Threats / Total Threats | **100%** (Every missed threat can be devastating). |

---

## ⏱️ Time-Based Metrics (SLA)
Service Level Agreements (SLAs) define the acceptable timeframes for handling security incidents.

* **MTTD (Mean Time to Detect):** Average time between the actual attack and its detection by SOC tools.
* **MTTA (Mean Time to Acknowledge):** Average time from when an alert is generated to when an L1 analyst starts investigating it.
* **MTTR (Mean Time to Respond):** Average time taken by the SOC team to fully stop the breach from spreading, measured from the moment the alert was generated.

---

## 🛠️ Common Scenarios & Remediation Strategies

As a SOC L1 Analyst or SOC Manager, identifying bottlenecks in these metrics is crucial. Here are common issues and their engineering solutions:

### Scenario 1: High MTTR (Delayed Response)
* **Problem:** Analysts take too long to contain an attack (e.g., resetting breached credentials).
* **Solution:** Create and distribute detailed **Workbooks/Playbooks** outlining step-by-step procedures for specific incident types to reduce hesitation and research time.

### Scenario 2: High MTTD (Delayed Detection)
* **Problem:** An attack occurs, but the SIEM takes 20+ minutes to generate an alert.
* **Solution:** Assign a **SOC Engineer** to tune the SIEM and detection rules to run more frequently (e.g., every 5 minutes instead of every 30 minutes).

### Scenario 3: High FPR (Alert Fatigue / Tired Analysts)
* **Problem:** Analysts are closing hundreds of alerts, with 95% being IT system noise.
* **Solution:** Implement a **False Positive Remediation** process. Assign SOC Engineers to exclude trusted system activity (whitelisting) from EDR/SIEM detection rules.

---
**Compiled by:** Piyangkoon Tongrujiroj (Frame)
**Focus:** SOC L1 / Cybersecurity Operations / SOC Metrics Management