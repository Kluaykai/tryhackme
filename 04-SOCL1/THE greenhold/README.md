# 🛡️ TryHackMe: Phishing Analysis - Greenholt PLC Incident

## 📝 Objective
This project demonstrates the methodology used to analyze and investigate a suspicious email reported by an employee. The goal is to determine the legitimacy of the email, extract key artifacts, investigate the source infrastructure, and analyze potential malicious attachments using Open-Source Intelligence (OSINT) and fundamental SOC Analyst techniques.

## 📖 Scenario
A sales executive at Greenholt PLC received an email from a known customer. However, the message contained several red flags: a generic greeting, an unexpected request for a money transfer, and an unsolicited attachment. The email was escalated to the Security Operations Center (SOC) as a potential phishing attempt. 

## 🛠️ Skills & Tools Demonstrated
*   **Email Header Analysis:** Reading and extracting artifacts from raw email sources (Sender, Reply-To, Originating IP).
*   **Infrastructure Investigation (OSINT):** Utilizing WHOIS and IP intelligence to identify hosting providers and attacker infrastructure.
*   **Email Security Protocols:** Querying and analyzing SPF and DMARC records to verify domain authenticity.
*   **Malware/Attachment Analysis:** Generating cryptographic hashes (SHA256) and utilizing Threat Intelligence platforms to investigate suspicious files.
*   **Tools Used:** Mozilla Thunderbird, Linux Command Line (`sha256sum`), IPinfo.io, MXToolbox, VirusTotal.

## 🔍 Investigation Steps & Findings

### 1. Artifact Extraction & Header Analysis
*   **Suspicious Sender Address:** The email display name spoofed a legitimate contact, but the `From` address was identified as `info@mutawamarine.com`.
*   **Reply-To Anomaly:** The `Reply-To` address was set to `info.mutawamarine@mail.com` (a free email provider), a classic technique to route replies back to the attacker.
*   **Originating IP:** Extracted from the `Received` headers, the originating IP was identified as `192.119.71.157`.

### 2. Infrastructure & Domain OSINT
*   **IP Ownership:** OSINT investigation revealed the IP `192.119.71.157` belongs to **Hostwinds LLC.**, indicating the attacker likely rented a VPS to conduct the campaign.
*   **Domain Security Records:** 
    *   **SPF Record:** `v=spf1 include:spf.protection.outlook.com -all`
    *   **DMARC Record:** `v=DMARC1; p=quarantine; fo=1`
    *   *Analysis:* While the domain has security records configured, the email was sent from an unauthorized infrastructure (Hostwinds) not listed in the SPF record, confirming it as a spoofed/phishing email.

### 3. Attachment Analysis
*   **File Identification:** The email contained an attachment named `SWT_#09674321____PDF__.CAB`. The double extension (`.PDF__.CAB`) is a common technique to deceive users.
*   **Hashing:** The file was extracted and hashed using the Linux terminal.
    *   **SHA256:** `2e91c533615a9bb8929ac4bb76707b2444597ce063d84a4b33525e25074fff3f`
*   **Threat Intelligence (VirusTotal):** Analyzing the hash revealed the true file size is `400.26 KB` and the actual file type is a `rar` archive, hiding the potentially malicious payload inside.

## 💡 Conclusion
The investigation confirms that the email is a targeted phishing attempt. The attacker spoofed a known business domain, routed responses to a look-alike free email account, utilized a rented VPS for transmission, and attached a disguised archive file to bypass initial scrutiny.