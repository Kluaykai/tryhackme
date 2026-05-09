# 🛡️ The Unified Kill Chain (UKC)

A modern and highly detailed framework developed by Paul Pols in 2017 (updated in 2022) to help understand how cyber attacks occur. It complements other frameworks like MITRE ATT&CK by providing a realistic, 18-phase attack model where attackers can move back and forth between phases.
(โมเดลวิเคราะห์การโจมตีทางไซเบอร์ที่พัฒนาโดย Paul Pols ในปี 2017 ซึ่งละเอียดและสมจริงกว่าแบบเก่า โดยแบ่งออกเป็น 18 ขั้นตอน และสามารถทำงานร่วมกับ MITRE ATT&CK ได้เป็นอย่างดี)

---

## 🎯 The 3 Main Goals of UKC (เป้าหมายหลัก 3 ส่วน)

### 1. In (Initial Foothold - การเจาะเข้าระบบ)
The main focus is for an attacker to gain access to a system or networked environment.
(ขั้นตอนการหาช่องโหว่และเจาะทะลวงด่านแรกเพื่อสร้างจุดยืนในระบบ)
* **Reconnaissance:** Gathering info about the target (สืบข้อมูลเป้าหมาย).
* **Weaponization:** Setting up the attack infrastructure like C2 servers (เตรียมอาวุธและเซิร์ฟเวอร์สั่งการ).
* **Social Engineering:** Manipulating employees, e.g., Phishing (หลอกลวงพนักงาน เช่น ส่งอีเมล Phishing).
* **Exploitation:** Abusing vulnerabilities to execute code (เจาะช่องโหว่เพื่อรันโค้ดอันตราย).
* **Persistence:** Maintaining access, e.g., leaving a backdoor (ฝังตัว สร้างทางเข้าลับ).
* **Defense Evasion:** Bypassing firewalls and AV (หลบหลีกระบบป้องกันภัย).
* **Command & Control (C2):** Communicating with the compromised system (เชื่อมต่อเพื่อสั่งการ).
* **Pivoting:** Using the compromised system to reach others (ใช้เครื่องเหยื่อเป็นฐานกระโดดไปเครื่องอื่น).

### 2. Through (Network Propagation - การขยายผลและทะลวงเครือข่าย)
Seeking to gain additional access, privileges, and move laterally through the network.
(ขั้นตอนการขยายสิทธิ์และเจาะลึกเข้าไปในเครือข่ายภายใน)
* **Discovery:** Uncovering info about the internal network and permissions (สำรวจเครือข่ายภายในและสิทธิ์ต่างๆ).
* **Privilege Escalation:** Gaining higher permissions like Admin/ROOT (ยกระดับสิทธิ์ให้กลายเป็นแอดมิน).
* **Execution:** Deploying malicious code/tools on the pivot system (รันเครื่องมือหรือมัลแวร์เพิ่มเติม).
* **Credential Access:** Stealing passwords, e.g., using Mimikatz (ขโมยรหัสผ่านของผู้ใช้คนอื่น).
* **Lateral Movement:** Jumping onto other targeted systems using stolen credentials (มุดข้ามไปยังเครื่องอื่นๆ ในเครือข่าย).

### 3. Out (Action on Objectives - การบรรลุเป้าหมาย)
Fulfilling the attack goals, usually compromising the Confidentiality, Integrity, and Availability (CIA) triad.
(ขั้นตอนสุดท้ายในการกอบโกยผลประโยชน์หรือทำลายระบบ)
* **Collection:** Gathering valuable data of interest (รวบรวมข้อมูลสำคัญที่ต้องการขโมย).
* **Exfiltration:** Stealing and transferring data out of the network (ลักลอบส่งข้อมูลออกไปข้างนอก).
* **Impact:** Disrupting business, e.g., deploying Ransomware or deleting files (ทำลายระบบ เช่น ปล่อย Ransomware เรียกค่าไถ่).
* **Objectives:** Achieving the strategic/financial goals (บรรลุเป้าหมายสูงสุดของแฮกเกอร์).

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC Analyst Foundation / Threat Intelligence / Incident Response