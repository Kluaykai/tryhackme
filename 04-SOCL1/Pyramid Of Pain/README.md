# 🔺 The Pyramid of Pain

A foundational concept in Threat Intelligence and SOC Operations. The Pyramid of Pain measures how much "pain" or difficulty we cause an adversary when we detect and deny their indicators of compromise (IOCs). The higher up the pyramid we detect them, the harder it is for them to attack us.

## 📊 The Levels of the Pyramid (From Bottom to Top)

### 1. Hash Values (Trivial / แก้เกมง่ายมาก)
* **What it is:** Digital fingerprints of files (e.g., MD5, SHA-1, SHA-256).
* **Attacker's Pain:** Trivial. They just need to change a single bit (like adding a space) in their malware to generate a completely new hash, bypassing our blocklist instantly.

### 2. IP Addresses (Easy / แก้เกมง่าย)
* **What it is:** The network address used for the attack or Command & Control (C2).
* **Attacker's Pain:** Easy. They can easily switch to a new proxy, VPN, or use techniques like **Fast Flux** (rapidly changing hundreds of IPs for a single domain) to evade IP blocking.

### 3. Domain Names (Simple / เริ่มมีขั้นตอน)
* **What it is:** The website addresses used for hosting malware or C2 (e.g., `evilcorp.com`).
* **Attacker's Pain:** Simple. It takes a bit more effort to buy, register, and setup DNS for new domains. Attackers often use **Punycode** (using foreign characters to fake famous sites like `adıdas.de`) or **URL Shorteners** to hide malicious domains.

### 4. Network/Host Artifacts (Annoying / น่ารำคาญ)
* **What it is:** The specific traces left behind on the system or network.
  * *Host Artifacts:* Dropped files, modified registry keys, weird processes (`regidle.exe`).
  * *Network Artifacts:* Specific `User-Agent` strings in HTTP requests, unique URI patterns.
* **Attacker's Pain:** Annoying. If we block these, the attacker has to go back and rewrite parts of their malware to change how it communicates or hides in the machine.

### 5. Tools (Challenging / ท้าทาย)
* **What it is:** The actual software/utilities the attackers use to execute the attack (e.g., Cobalt Strike, Mimikatz, password crackers).
* **Defense Tech:** We use **Fuzzy Hashing** (like **SSDeep**) to detect variations of the same tool, even if they tweak the code slightly.
* **Attacker's Pain:** Challenging. They must invest significant time, effort, and money to build or buy entirely new tools to bypass our defenses.

### 6. TTPs - Tactics, Techniques & Procedures (Tough / สาหัส)
* **What it is:** The *behavior*, *habits*, and *strategies* of the attacker (typically mapped to the **MITRE ATT&CK Framework**). For example, their specific method of stealing passwords (Pass-the-Hash) or stealing data (Exfiltration).
* **Attacker's Pain:** Tough! If we detect and block their core methodology, their tools and infrastructure don't matter anymore. They have to completely unlearn and relearn how to hack. **This is the ultimate goal of a Blue Team / SOC Analyst!**

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC Analyst Foundation / Threat Intelligence / Incident Response