# 🎣 TryHackMe: Snapped Phishing Line - Incident Response Write-up

## 📝 Overview
This document outlines the incident response and investigation of a phishing campaign. The adversary utilized a malicious email attachment to redirect targets to a credential-harvesting website impersonating Microsoft Office 365. 

## 🛠️ Tools & Techniques Used
*   **Web Analysis:** Firefox (Directory Traversal / Directory Listing)
*   **Command Line Tools:** `sha256sum`, `grep`, `unzip`
*   **Threat Intelligence:** VirusTotal
*   **Data Decryption:** CyberChef

---

## 🔍 Investigation Steps & Findings

### 1. URL & Infrastructure Analysis
*   Analyzed the suspicious email attachment and extracted the redirection URL.
*   **Malicious Root Domain:** `kennaroads.buzz`
*   **Impersonated Entity:** Microsoft

### 2. Phishing Kit Discovery
*   Exploited a misconfigured web server (Directory Listing) by navigating to the `/data/` directory.
*   Discovered and downloaded the adversary's phishing kit archive: `Update365.zip`

### 3. Static File Analysis (VirusTotal)
*   Generated the SHA256 hash of the phishing kit using the terminal.
*   Queried the hash on VirusTotal to avoid executing the payload locally.
*   **Threat Category:** `trojan`
*   **Archive Contents:** The archive contained exactly `49` files.

### 4. Impact Assessment (Compromised Credentials)
*   Navigated further into the exposed directory (`/data/Update365/`) to locate credential logs left public by the adversary.
*   Identified compromised users.
*   **Target who submitted credentials multiple times:** `michael.ascot@swiftspend.finance`

### 5. Threat Actor Attribution (Code Review)
*   Extracted the PHP source code from the phishing kit to identify the exfiltration endpoints.
*   Used `grep` to parse the code for email addresses.
*   **Adversary Email (Yandex):** `m3npat@yandex.com`
*   **Adversary Email (Gmail):** `jamestanner2299@gmail.com`

### 6. Flag Recovery
*   Located a hidden `flag.txt` file within the open directories.
*   Decoded the reversed string using CyberChef.
*   **Secret Value:** `THM{pL4y_w1Th_tH3_URL}`

---
**Status:** Investigation Closed 🔒