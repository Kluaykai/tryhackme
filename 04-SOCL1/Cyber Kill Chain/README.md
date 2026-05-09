# ⛓️ The Cyber Kill Chain (วงจรการโจมตีทางไซเบอร์)

A framework developed by Lockheed Martin to identify and prevent cyber intrusions activity. The model identifies what the adversaries must complete in order to achieve their objective.
(โมเดลที่คิดค้นโดย Lockheed Martin เพื่อใช้วิเคราะห์และป้องกันการโจมตีทางไซเบอร์ โดยแบ่งขั้นตอนที่แฮกเกอร์ต้องทำเพื่อให้การโจมตีสำเร็จออกเป็น 7 ขั้นตอน)

---

## 🎯 The 7 Phases of the Cyber Kill Chain

### 1. Reconnaissance (การลาดตระเวนและหาข้อมูล)
* **English:** The research and planning phase. Adversaries gather information about their target using OSINT (Open-Source Intelligence), email harvesting, and tools like `theHarvester`.
* **Thai:** ขั้นตอนการสืบข้อมูลเป้าหมาย แฮกเกอร์จะรวบรวมข้อมูลผ่านช่องทางสาธารณะ (OSINT) เช่น หาอีเมลพนักงาน โครงสร้างองค์กร เพื่อใช้ในการวางแผนโจมตี

### 2. Weaponization (การสร้างอาวุธ)
* **English:** Turning the gathered information into actionable attack tools. This includes crafting malware, exploits, or malicious Office documents containing VBA **macros**.
* **Thai:** นำข้อมูลที่ได้มาสร้างเครื่องมือเจาะระบบ เช่น เอาโค้ดอันตรายไปซ่อนไว้ในไฟล์ Word/Excel (Macro) หรือสร้างมัลแวร์เฉพาะกิจขึ้นมา

### 3. Delivery (การส่งมอบอาวุธ)
* **English:** Transmitting the payload to the target environment. Common methods include **Spearphishing** emails, USB drops, and **Watering hole attacks** (infecting frequently visited websites).
* **Thai:** ส่งไฟล์ไวรัสหรือลิงก์อันตรายไปให้เป้าหมาย เช่น ส่งอีเมลหลอกลวง (Phishing), แกล้งทำแฟลชไดรฟ์ตกไว้ (USB Drops) หรือดักฝังไวรัสในเว็บที่เป้าหมายเข้าบ่อยๆ

### 4. Exploitation (การเจาะระบบ)
* **English:** The moment the attacker's code executes on the target, taking advantage of known vulnerabilities or **Zero-day exploits** (flaws unknown to the vendor).
* **Thai:** วินาทีที่แฮกเกอร์ลั่นไก! โค้ดอันตรายจะถูกรันโดยอาศัยช่องโหว่ของโปรแกรมในเครื่องเหยื่อ (รวมถึงช่องโหว่ที่ยังไม่มีใครเคยเจอมาก่อนอย่าง Zero-day)

### 5. Installation (การฝังตัวและสร้างประตูหลัง)
* **English:** Installing a persistent backdoor to maintain access even if the system is rebooted. Attackers may use **Timestomping** to hide modified files or install a **Web shell** on servers.
* **Thai:** สร้างทางเข้าลับ (Backdoor) ทิ้งไว้ เผื่อคอมดับหรือโดนตัดเน็ตจะได้กลับเข้ามาได้อีก แฮกเกอร์มักจะแก้เวลาของไฟล์ (Timestomping) เพื่อตบตาคนตรวจสอบ

### 6. Command and Control (การสั่งการและควบคุม - C2)
* **English:** Establishing a communication channel between the compromised host and the attacker's server. Techniques include **DNS Tunneling** to evade firewalls.
* **Thai:** เครื่องของเหยื่อจะแอบต่อสายตรงกลับไปหาเซิร์ฟเวอร์ของแฮกเกอร์ (C2) เพื่อรอรับคำสั่งต่อไป โดยอาจซ่อนข้อมูลไปกับระบบปกติเช่น DNS (DNS Tunneling)

### 7. Actions on Objectives (การลงมือตามเป้าหมาย)
* **English:** Achieving the final goals, such as data exfiltration, lateral movement, or ransomware deployment. Attackers often delete **Shadow Copies** to prevent system restoration.
* **Thai:** ลงมือเก็บเกี่ยวผลประโยชน์ เช่น ขโมยข้อมูลลูกค้า, ทำลายระบบ, หรือลบไฟล์แบ็คอัพสำรอง (Shadow Copy) ทิ้งเพื่อปล่อย Ransomware เรียกค่าไถ่

---

## 📝 Real-World Case Study: Target Data Breach (2013)
* **Weaponization:** PowerShell scripts.
* **Delivery:** Spearphishing attachment sent to a third-party vendor.
* **Exploitation:** Exploiting a public-facing application.
* **Installation:** Dynamic linker hijacking to maintain stealthy access.
* **Command & Control:** Fallback channels for persistent communication.
* **Actions on Objectives:** Stole credit card data from local systems (40 million accounts impacted).

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC Analyst Foundation / Threat Intelligence / Incident Response