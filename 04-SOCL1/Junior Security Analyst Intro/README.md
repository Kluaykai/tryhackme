## 1. Introduction to SOC (Security Operations Center)
ในฐานะ Junior Security Analyst (SOC Level 1) หน้าที่หลักคือการเป็น "ปราการด่านหน้า" ตรวจสอบการแจ้งเตือน (Alerts) คัดกรองทราฟฟิก และหยุดยั้งภัยคุกคามก่อนที่จะสร้างความเสียหายให้องค์กร โดยการทำงานใน SOC จะต้องประสานงานกับผู้เชี่ยวชาญในหลายส่วน ดังนี้:

**SOC Team Roles & Responsibilities:**
*   **Junior Analyst (L1):** เฝ้าระวังแดชบอร์ด ตรวจสอบ Alerts เบื้องต้น และจัดการ Ticket ในแต่ละวัน
*   **Senior Analyst (L2/L3):** (เช่น Will Griffin) รับช่วงต่อ (Escalate) ในเคสที่มีความซับซ้อนสูง และเป็นที่ปรึกษาให้ L1
*   **SOC Engineer:** ดูแล ปรับแต่ง และบำรุงรักษาเครื่องมือ Security Tools ให้พร้อมใช้งาน
*   **SOC Manager:** ควบคุมภาพรวมการทำงานของทีม และรายงานสรุปผลการป้องกันภัยคุกคามต่อผู้บริหาร
*   **Incident Responder (IR):** ผู้เชี่ยวชาญพิเศษที่จะถูกเรียกตัวมาจัดการเฉพาะเมื่อเกิดเหตุการณ์โจมตีระดับรุนแรง (Major Incidents)

**Basic Alert Triage Workflow (กระบวนการตอบสนองต่อภัยคุกคามเบื้องต้น):**
จากการจำลองสถานการณ์หน้าแดชบอร์ด (Lab Simulation) กระบวนการทำงานพื้นฐานเมื่อพบเหตุการณ์น่าสงสัย มีสเต็ปดังนี้:
1.  **Monitor & Identify:** ตรวจพบทราฟฟิกที่ผิดปกติจากแดชบอร์ด และระบุค่า IOC (Indicator of Compromise) เช่น Malicious IP Address
2.  **Escalate:** ส่งเรื่องต่อให้ Senior Analyst (Will Griffin) เพื่อประเมินความเสี่ยงเชิงลึก
3.  **Containment:** ทำการระงับเหตุเบื้องต้น เช่น การสั่ง **Block IP** บนระบบ Firewall เพื่อตัดการเชื่อมต่อจากผู้โจมตีทันที
4.  **Resolution:** ตรวจสอบความสำเร็จของการบล็อก (รับ Flag `THM{until-we-meet-again}`) และบันทึกผลการดำเนินงานลงระบบ