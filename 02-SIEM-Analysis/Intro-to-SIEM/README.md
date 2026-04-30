# 🛡️ Write-up: Introduction to SIEM (TryHackMe)

ในห้องนี้ผมได้เรียนรู้พื้นฐานที่สำคัญที่สุดของงาน SOC คือการเข้าใจว่าระบบ **SIEM (Security Information and Event Management)** ทำหน้าที่เป็นศูนย์กลางในการรวบรวมข้อมูลเพื่อตรวจจับและตอบสนองต่อภัยคุกคามอย่างไร

## 📚 Key Concepts Learned

### 1. Log Sources & Visibility
ข้อมูลที่ไหลเข้าสู่ SIEM มาจาก 2 แหล่งหลัก:
- **Host-Centric Logs:** บันทึกพฤติกรรมภายในเครื่อง เช่น การรันโปรแกรม (Process Creation) หรือการแก้ไขไฟล์
- **Network-Centric Logs:** บันทึกการเชื่อมต่อในเครือข่าย เช่น เว็บไซต์ที่พนักงานเข้าถึง หรือการเชื่อมต่อ VPN

### 2. The SIEM Workflow
- **Log Ingestion:** การนำข้อมูลเข้าผ่านตัวกลางที่เรียกว่า **Agent** หรือ **Forwarder**
- **Normalization:** การปรับรูปแบบ Log ที่มาจากหลายยี่ห้อ (Windows, Linux, Firewall) ให้เป็นมาตรฐานเดียวกัน
- **Correlation:** หัวใจหลักของ SIEM คือการนำ Log จากหลายแหล่งมาเชื่อมโยงกันเพื่อหาพฤติกรรมที่น่าสงสัย (เช่น มีการล็อกอินผิดปกติ + มีการรันโปรแกรมแปลกๆ)

### 3. Alert Investigation
เมื่อ SIEM แจ้งเตือน (Trigger Alert) นักวิเคราะห์ต้องแยกแยะระหว่าง:
- **True Positive:** ภัยคุกคามของจริง ต้องรีบรับมือ (Remediation)
- **False Positive:** ระบบเตือนผิดพลาด ต้องทำการปรับจูนกฎ (Tuning)

---

## 🕵️ Lab Case Study: Investigating a Potential Threat

ในแล็บจำลองนี้ ผมได้สืบสวน Alert **"Potential CryptoMiner Activity"** จากข้อมูลใน SIEM Dashboard และได้ข้อสรุปดังนี้:

- **Suspect Process:** `cudominer.exe` (โปรแกรมขุดเหรียญคริปโต)
- **Target User:** `chris.fort`
- **Infected Host:** `HR_02`
- **Detection Logic:** ระบบตรวจจับคำว่า `miner` ในชื่อ Process ที่รันบน Windows (Event ID 4688)
- **Outcome:** **True Positive** - เครื่องคอมพิวเตอร์ในแผนก HR ถูกใช้เพื่อขุดคริปโตอย่างผิดกฎบริษัท

---

## 🖼️ Evidence (Screenshots)

![SIEM Dashboard Analysis](./assets/siem-lab-result.png)
*ภาพประกอบ: หน้าจอการวิเคราะห์เหตุการณ์ในแล็บจำลอง*