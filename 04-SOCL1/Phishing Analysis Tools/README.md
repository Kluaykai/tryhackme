🛡️ README: Phishing Analysis Tools (TryHackMe)
🎯 Objective
เรียนรู้การวิเคราะห์อีเมลฟิชชิ่ง (Phishing Emails) และไฟล์แนบต้องสงสัย (Malicious Attachments) โดยใช้เครื่องมืออัตโนมัติและระบบ Sandbox เพื่อสกัดหา Indicators of Compromise (IOCs) เช่น IP, Domain, และค่า Hash สำหรับนำไปสร้างกฎการตรวจจับ (Detection Rules)

🛠️ Tools & Platforms Used
PhishTool: แพลตฟอร์มวิเคราะห์อีเมลแบบ All-in-one ช่วยสกัด Email Headers, URLs, และไฟล์แนบอัตโนมัติ พร้อมเชื่อมต่อกับ VirusTotal เพื่อเช็ก Threat Intelligence

VirusTotal: ระบบตรวจสอบประวัติความน่าเชื่อถือของไฟล์และลิงก์จากฐานข้อมูลแอนตี้ไวรัสหลายสิบสำนัก

ANY.RUN: Interactive Malware Sandbox สำหรับทำ Dynamic Analysis ทำให้เราสามารถโต้ตอบกับมัลแวร์ในสภาพแวดล้อมจำลองแบบ Real-time เพื่อดูพฤติกรรม Network และ Process Tree

Hybrid Analysis / JOESandbox: ระบบ Sandbox เพิ่มเติมที่ให้ข้อมูลเชิงลึกทั้งแบบ Static และ Dynamic

🔍 Key Techniques (SOC Analyst Skills)
Email Header Analysis:

ตรวจสอบบรรทัด Received: from เพื่อหา IP Address ต้นทางที่แท้จริง

ตรวจสอบบรรทัด Return-Path เพื่อหาโดเมนที่แฮกเกอร์ใช้รับอีเมลตีกลับ

Defanging & Artifact Extraction:

การแยกแยะระหว่าง Brand ที่ถูกปลอมแปลง (เช่น Netflix) กับโดเมนจริงของแฮกเกอร์

การดึง Shortened URLs ที่ซ่อนอยู่ใต้ปุ่ม Call-to-action

Sandbox Analysis (Dynamic Analysis):

ดึงค่า SHA256 Hash จากไฟล์ต้องสงสัย (เช่น .pdf หรือ .xlsx) เพื่อใช้เป็นลายนิ้วมือดิจิทัล

วิเคราะห์ Network Connections ดูว่า Process ของ Windows ตัวไหนพยายามวิ่งออกไปหา Malicious IP / Domains

สังเกตเทคนิคการพรางตัว (Obfuscation) เช่น การสะกดคำผิดในไฟล์ (เช่น vpdate, vovr) เพื่อหลบระบบกรองคำของอีเมล

🚨 Noteworthy Threats & Exploits
Malicious PDF (AcroRd32.exe): ไฟล์ PDF ที่ฝังคำสั่งให้โปรแกรม Adobe Reader แอบเชื่อมต่อเครือข่ายไปยัง IP ของแฮกเกอร์

Malicious Excel (CVE-2017-11882): ไฟล์ .xlsx ที่พยายามโจมตีช่องโหว่ Memory Corruption ใน Microsoft Office Equation Editor (EQNEDT32.EXE) เพื่อดาวน์โหลดมัลแวร์จากโดเมนภายนอก (เช่น biz9holdings.com)

📝 Note for SOC Interviews
"ในการทำงานจริง แต่ละ Security Vendor อาจให้ผลการตรวจจับที่ต่างกัน (เช่น 1/94 ใน VirusTotal) เนื่องจากความเร็วในการอัปเดต Threat Intel และเทคนิคการสแกนที่ต่างกัน (Signature-based vs. Behavior-based) ดังนั้น SOC Analyst จึงต้องพึ่งพา Sandbox อย่าง ANY.RUN เพื่อยืนยันพฤติกรรมด้วยตาตัวเองเสมอ"