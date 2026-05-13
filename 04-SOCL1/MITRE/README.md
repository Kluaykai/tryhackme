# 🛡️ MITRE Advanced Frameworks & Tools

Beyond the standard ATT&CK framework, MITRE provides specialized tools and knowledge bases to help defenders build countermeasures, test their systems, and secure emerging technologies like Blockchain and AI.
(นอกเหนือจาก ATT&CK แล้ว MITRE ยังมีเครื่องมือและเฟรมเวิร์กขั้นสูงเพื่อช่วยทีมรับมือภัยคุกคามในการสร้างระบบป้องกัน ทดสอบระบบ และรับมือกับเทคโนโลยีใหม่ๆ อย่าง Blockchain และ AI)

---

## 🛡️ 1. MITRE D3FEND (The Defender's Playbook)
While ATT&CK shows how attackers attack, D3FEND shows how defenders must defend. It is a framework that maps out defensive techniques and countermeasures.
(ถ้า ATT&CK คือตำราของฝั่งโจมตี D3FEND ก็คือตำราของฝั่งป้องกัน รวบรวมเทคนิคและวิธีการตั้งรับต่างๆ เช่น การตั้งค่าความปลอดภัยของระบบ)
*   **Focus:** Detection, Denial, and Disruption (ตรวจจับ สกัดกั้น และขัดขวาง)
*   **Example:** Analyzing Network Traffic to detect abnormal User Geolocation Logon Patterns.

## ⚔️ 2. Emulation & Testing Tools (เครื่องมือจำลองการโจมตี)
*   **Adversary Emulation Library (by CTID):** A free resource containing step-by-step plans to mimic real-world APT groups (คู่มือสอนจำลองการโจมตีแบบ Step-by-step ตามรอยกลุ่มแฮกเกอร์ระดับโลก).
*   **Caldera:** An automated adversary emulation tool used for both red and blue team exercises to test and enhance defenses (โปรแกรมอัตโนมัติที่ใช้จำลองการโจมตีเพื่อทดสอบว่าระบบป้องกันของเราทำงานได้ดีแค่ไหน).

## 🚀 3. Emerging Technology Frameworks (เฟรมเวิร์กสำหรับเทคโนโลยีแห่งอนาคต)
As technology evolves, MITRE releases specific matrices to track new types of attacks.
(เมื่อเทคโนโลยีเปลี่ยนไป MITRE ก็สร้างตารางแบบใหม่มาครอบคลุมการโจมตีเหล่านั้นด้วย)

*   **🪙 AADAPT (Adversarial Actions in Digital Asset Payment Technologies):**
    *   **Focus:** Blockchain networks, smart contracts, and digital wallets.
    *   **Example Technique:** Scraping Blockchain Data to gather intel on wallets.
*   **🤖 ATLAS (Adversarial Threat Landscape for Artificial-Intelligence Systems):**
    *   **Focus:** Threats targeting AI and Machine Learning systems (เช่น LLMs).
    *   **Example Technique:** LLM Prompt Obfuscation (ซ่อนเร้นคำสั่งอันตรายเพื่อหลอกระบบ AI).

---
**Compiled by:** Piyangkoon (Frame) Tongrujiroj
**Focus:** SOC Analyst Foundation / Threat Intelligence / Incident Response